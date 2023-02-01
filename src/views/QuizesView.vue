<script setup>
import q from "../data/quizes.json"
import {ref, watch} from "vue"
import Card from "../component/Card.vue"

  const quizzes = ref(q);
  const search  =ref("");

  watch(search, () => {
    quizzes.value = q.filter(quizz => quizz.name.toLowerCase().includes(search.value.toLowerCase()))
  })

</script>
<template>
    <header>
      <h1>Quizz</h1>
      <input v-model.trim="search" type="text" placeholder="Search ...">
    </header>
    <div class="options-container">
      <!-- <div v-for="quiz in quizzes" :key="quiz.id" class="card">
        <img :src="quiz.img" alt="">
        <div class="card-text">
          <h2>{{quiz.name}}</h2>
          <p>{{ quiz.questions.length }} questions</p>
        </div>
      </div> -->
      <Card v-for="quiz in quizzes" :key="quiz.id" :quiz="quiz"/>
    </div>
</template>
<style scoped>


header {
  margin-bottom: 10px;
  margin-top: 30px;
  display: flex;
  align-items: center;
}

header h1 {
  font-weight: bold;
  margin-right: 30px;
}

header input {
  border: none;
  padding: 10px;
  border-radius: 5px;
}

.options-container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap; 
  margin-top: 40px;
}



</style>