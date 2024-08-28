<script setup>
import QuizHeader from '@/components/QuizHeader.vue'
import QuizSection from '@/components/QuizSection.vue'
import QuizResult from '@/components/QuizResult.vue';
import { useRoute } from 'vue-router';
import { computed, ref, watch } from 'vue'
import quizes from '../data/quizes.json'

const route = useRoute()
const quizId = parseInt(route.params.id)
const quiz = quizes.find((q) => q.id === quizId)
const numberOfCorrectAnswer = ref(0)

const currentQuestionIndex = ref(0)
const showResult = ref(false)

const questionPage = computed (() => {
    return `${currentQuestionIndex.value + 1} / ${ quiz.questions.length }`
})

const barPercentage = computed (() => {
    return `${((currentQuestionIndex.value + 1) / quiz.questions.length) * 100}%`
})

function onSelectOption(answer){
    if(answer.correct){
        numberOfCorrectAnswer.value++
    }

    if(currentQuestionIndex.value === quiz.questions.length - 1 ){
        showResult.value = true
        return 
    }

    currentQuestionIndex.value++
}

</script>

<template>
    <QuizHeader :questionPage="questionPage" :barPercentage="barPercentage"></QuizHeader>
    <QuizSection :question="quiz.questions[currentQuestionIndex]" @selectOption="onSelectOption" v-if="!showResult"></QuizSection>
    <QuizResult v-else :quizQuestionsLength="quiz.questions.length" :quizCorrectAnswer="numberOfCorrectAnswer"></QuizResult>
</template> 

