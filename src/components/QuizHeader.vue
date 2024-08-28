<script setup>
import { defineProps } from 'vue';

const { questionPage } = defineProps(['questionPage'])
</script>

<template>
    <header>
        <h4>{{ questionPage }}</h4>
        <div class="bar">
            <div class="bar-progress"></div>
        </div>
    </header>
</template>

<style scoped>
header {
    margin-top: 20px;
}

header h4 {
    font-size: 30px;
}

.bar {
    width: 100%;
    height: 50px;
    border: 3px solid #9CA986;
}

.bar-progress {
    height: 100%;
    width: 50%;
    background-color: #9CA986;
}
</style>