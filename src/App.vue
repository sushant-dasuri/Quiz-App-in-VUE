<script setup>
 import q from "./data/quizzes.json";
 import {ref, watch} from "vue";

 const quizzes = ref(q);
 const search = ref("");

 watch(search, () => {
   quizzes.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
 })
</script>

<template>
  <div class="container">
    <header>
      <h1>
        Quizzes
      </h1>
      <input v-model.trim="search" type="text">
    </header>
    <div class="options-container">
      <div v-for="quiz in quizzes" :key="quiz.id" class="card">
        <img :src="quiz.img" alt="" />
        <div class="card-text">
          <h2>{{quiz.name}}</h2>
          <p>{{quiz.questions.length}} questions</p>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped>
 .container {
    max-width: 1000px;
    margin: 0 auto;
    padding-left: 20px;
  }
  header{
    margin: 30px 0 10px 0;
    display:flex;
    align-items: center;
  }
  header h1{
    font-weight: bold;
    margin-right: 30px;
  }
  header input{
    width: 200px;
    border: none;
    border-radius: 5px;
    background-color: #aaaaaa1a;
    /* opacity: 0.1; */
    padding: 10px;
    color: #000000ff;
  }
  header .btn-clear{
    margin-left:5px;
    border: none;
    font-weight: bold;
    background-color: #fff;
  }
  .btn-clear:hover{
    font-size: 1.2rem;
    color: red;
    margin-left: 4px;
  }
  .card-container{
    display: flex;
    flex-wrap: wrap;
    margin-top: 40px;
  }

  .options-container {
    display: flex;
    flex-wrap: wrap;
    margin-top: 40px;
  }

  /* CARD */
  .card {
    width: 300px;
    overflow: hidden;
    border-radius: 2%;
    box-shadow: 1px 1px 10px rgba(0,0,0,0.1);
    margin-bottom: 35px;
    margin-right: 20px;
    cursor: pointer;

  }

  .card img {
    width: 100%;
    height: 150px;
    margin: 0;
  }

  .card .card-text {
    padding: 0px 5px;
  }

  .card .card-text h2 {
    font-weight: bold;
  }
  
</style>