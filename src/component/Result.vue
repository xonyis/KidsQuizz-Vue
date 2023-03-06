<script setup>
import { defineProps } from 'vue'
import {RouterLink} from 'vue-router'
    const {quizQuestionLength, numberOfCorrectAnswers} = defineProps(["quizQuestionLength", "numberOfCorrectAnswers"])
</script>
<template>
    <div class="results">
        <p>Vos Résulats ...</p>
        <h1>
           {{ numberOfCorrectAnswers }} /{{ quizQuestionLength }}
        </h1>
        <RouterLink class="btnGBH" to="/">Retour a l'acceuil ...</RouterLink>
    </div>
</template>
<style scoped>
.results {
    text-align: center;
    padding: 100px 0;
}

p{
    font-size: 25px;
}

h1{
    font-size: 80px;
}
.btnGBH{
    font-size: 25px;
    text-decoration: none;
    color: wheat;
}
</style>