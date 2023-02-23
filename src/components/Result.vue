<script setup>
import {defineProps} from "vue"
import {RouterLink} from "vue-router"

const {numberOfCorrectAnswers, quizQuestionLength} = defineProps(['numberOfCorrectAnswers', 'quizQuestionLength']);
</script>
<template>
    <div class="results">
        <p>
           Your Results...
        </p>
        <h1>
            {{numberOfCorrectAnswers}}/{{quizQuestionLength}}
        </h1>
        <RouterLink to="/" class="go-back-btn">Go Back</RouterLink>
    </div>
</template>
<style scoped>
  .results {
      text-align: center;
      padding: 100px 0px;
  }

  p {
      font-size: 25px;
  }

  h1 {
      font-size: 80px;
  }

  .go-back-btn {
      width: 200px;
      height:60px;
      display: flex;
      justify-content: center;
      align-items: center;
      color: rgb(30, 28, 28);
      background-color: bisque;
      font-size: 25px;
      text-decoration: none;
      margin: 0 auto;
  }
  
</style>