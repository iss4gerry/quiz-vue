<script setup>
import { defineProps } from 'vue';

const { question } = defineProps(['question'])
</script>

<template>
    <section id="question-container">
        <h1 class="question-title">{{ question.text }}</h1>
    </section>
    <section id="option-container">
        <div class="option" v-for="answer in question.answers" :key="answer.id">
            <p class="option-label">{{ answer.label}}</p>
            <p class="option-value">{{ answer.text }}</p>
        </div>
    </section>
</template>

<style scoped>
#question-container {
    margin-top: 30px;
}

.question-title {
    font-size: 30px;
    font-weight: bold;
    margin-bottom: 20px;
}

.option {
    display: flex;
    align-items: center;
    cursor: pointer;
}

.option-label {
    font-size: 20px;
    font-weight: bold;
    width: 50px;
    height: 50px;
    background-color: #9CA986;
    display: flex;
    align-items: center;
    justify-content: center;
}

.option-value {
    font-size: 20px;
    font-weight: bold;
    padding: 0 20px;
    background-color: #C9DABF;
    width: 100%;
    height: 50px;
    display: flex;
    align-items: center;

}
</style>