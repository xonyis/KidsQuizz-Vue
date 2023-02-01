<script setup>
import { defineProps } from 'vue';
import { useRouter } from 'vue-router';
    const router = useRouter()
    const {quiz} = defineProps(['quiz'])

    const navigateToQuizz = () => {
      router.push(`/quiz/${quiz.id}`)
    }


</script>
<template>
    <div class="card" @click="navigateToQuizz">
        <img :src="quiz.img" alt="">
        <div class="card-text">
            <h2>{{quiz.name}}</h2>
            <p>{{ quiz.questions.length }} questions</p>
        </div>
    </div>
</template>
<style scoped>
/* CARD */

.card{
  width: 310px;
  border: 1px solid lightblue;
  overflow: hidden;
  border-radius: 2%;
  box-shadow: 1px 1px 10px rgba(255, 255, 255, 0.245);
  margin-bottom: 25px;
  margin-right: 20px;
  cursor: pointer;
}

.card img {
  width: 100%;
  height: 190px ;
  margin: 0;
}

.card .card-text {
  padding: 0 5px;
}

.card .card-text h2 {
   font-weight: bold;
}
</style>