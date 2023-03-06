<script setup>
import q from "../data/quizes.json"
import gsap from "gsap";
import {ref, watch} from "vue"
import Card from "../component/Card.vue"

  const quizzes = ref(q);
  const search  =ref("");

  watch(search, () => {
    quizzes.value = q.filter(quizz => quizz.name.toLowerCase().includes(search.value.toLowerCase()))
  })

  const beforEnter = (el) => {
    // card enter from
    el.style.opacity = 0;
    el.style.transform = "translateY(-20%)";
  }

  const enter = (el) => {
    // card enter to 
    gsap.to(el, {
       y: 0,
       opacity:1,
       duration: 0.5, 
       delay: el.dataset.index * 0.3
    })
  }
</script>
<template>
    <header>
      <h1>Quizz</h1>
      <input v-model.trim="search" type="text" placeholder="Search ...">
    </header>
    <div class="options-container">
      <TransitionGroup name="card" appear 
      @before-enter="beforEnter"
      @enter="enter"> 
        <Card 
        v-for="(quiz, index) in quizzes" :key="quiz.id" 
        :quiz="quiz"
        :data-index="index"
        />
      </TransitionGroup>
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