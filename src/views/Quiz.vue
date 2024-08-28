<script setup>
import QuizHeader from '@/components/QuizHeader.vue'
import QuizSection from '@/components/QuizSection.vue'
import { useRoute } from 'vue-router';
import { ref, watch } from 'vue'
import quizes from '../data/quizes.json'

const route = useRoute()
const quizId = parseInt(route.params.id)
const quiz = quizes.find((q) => q.id === quizId)

const currentQuestionIndex = ref(0)
const questionPage = ref(`${currentQuestionIndex.value + 1} / ${ quiz.questions.length }`)

watch(() => currentQuestionIndex.value,
      () => {
        questionPage.value = `${currentQuestionIndex.value + 1} / ${ quiz.questions.length }`
      }
)

</script>

<template>
    <QuizHeader :questionPage="questionPage"></QuizHeader>
    <QuizSection :question="quiz.questions[currentQuestionIndex]"></QuizSection>
    <button @click="currentQuestionIndex++" 
            :disabled="currentQuestionIndex === quiz.questions.length - 1">Next</button>
</template> 

