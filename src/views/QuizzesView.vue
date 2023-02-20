<script setup>
 import q from "../data/quizzes.json";
 import {ref, watch} from "vue";
 import Card from '../components/Card.vue';

 const quizzes = ref(q);
 const search = ref("");

 watch(search, () => {
   quizzes.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
 })
</script>

<template>
    <header>
      <h1>
        Quizzes
      </h1>
      <input v-model.trim="search" type="text">
    </header>
    <div class="options-container">
      <Card v-for="quiz in quizzes" :key="quiz.id" :quiz="quiz" />
    </div>
</template>
<style scoped>
 
  header {
    margin: 30px 0 10px 0;
    display:flex;
    align-items: center;
  }
  header h1 {
    font-weight: bold;
    margin-right: 30px;
  }
  header input {
    width: 200px;
    border: none;
    border-radius: 5px;
    background-color: #aaaaaa1a;
    /* opacity: 0.1; */
    padding: 10px;
    color: #000000ff;
  }
  header .btn-clear {
    margin-left:5px;
    border: none;
    font-weight: bold;
    background-color: #fff;
  }
  .btn-clear:hover {
    font-size: 1.2rem;
    color: red;
    margin-left: 4px;
  }
  .card-container {
    display: flex;
    flex-wrap: wrap;
    margin-top: 40px;
  }

  .options-container {
    display: flex;
    flex-wrap: wrap;
    margin-top: 40px;
  }
</style>