<script setup>
import { defineProps, defineEmits } from 'vue';

const emit = defineEmits(["selectOption"])

const {question} = defineProps(['question'])

const emitSelectedOption = (isCorrect) => {
    emit("selectOption", isCorrect)
}
</script>

<template>
    <div>
        <div class="question-container"> 
            <h1 class="question">
                {{question.text}}
            </h1>
        </div>
        <div class="option-container">
             <div v-for="option in question.options" :key="option.id" 
             class="option"
             @click="emitSelectedOption(option.isCorrect)">
                <p class="option-label">{{ option.label }}</p>
                <div class="option-values">
                    <p>{{option.text}}</p>
                </div>
             </div>
        </div>
    </div>
</template>

<style scoped>
.question-container {
        margin-top: 20px;
    }

    .question {
        font-size: 20px;
        margin-bottom: 20px;
    }
    .option {
        display: flex;
        margin-bottom: 20px;
        cursor: pointer;
    }

    .option-label {
        background: wheat;
        width: 50px;
        height: 50px;
        font-size: 30px;
        display: flex;
        align-items: center;
        justify-content: center;
        color: #121212;
    }
    .option-values {
        background: grey;
        width: 100%;
        font-size: 30px;
        padding: 0 20px;
    }
</style>