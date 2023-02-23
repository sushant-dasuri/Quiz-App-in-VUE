<script setup>
import Question from "../components/Question.vue";
import QuizHeader from "../components/QuizHeader.vue";
import Result from "../components/Result.vue";
import {useRoute} from "vue-router";
import quizzes from "../data/quizzes.json";
import { ref, watch, computed } from "vue";

const route = useRoute();
const quizId = parseInt(route.params.id);
const quiz = quizzes.find(q => q.id === quizId);
const currentQuestionIndex = ref(0);
const noOfCorrectAnswers = ref(0);
const showResult = ref(false);
/* const questionStatus = ref(`${currentQuestionIndex.value}/${quiz.questions.length}`)

watch(() => currentQuestionIndex.value, () => {
   questionStatus.value =  `${currentQuestionIndex.value}/${quiz.questions.length}`
}) */

const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`);
const barPercentage = computed(() => `${currentQuestionIndex.value / quiz.questions.length * 100}%`);
const selectOption = (isCorrect) => {
    if(isCorrect) {
        noOfCorrectAnswers.value++;
    }

    if(quiz.questions.length - 1 === currentQuestionIndex.value) {
        showResult.value = true;
    }
    currentQuestionIndex.value++;
}


</script>

<template>
    <QuizHeader
    :questionStatus="questionStatus"
    :barPercentage="barPercentage" />
    <div>
        <Question v-if="!showResult" :question= "quiz.questions[currentQuestionIndex]" :quiz= "quiz" @selectOption="selectOption" />
        <Result v-else :quizQuestionLength="quiz.questions.length" :numberOfCorrectAnswers="noOfCorrectAnswers" />
    </div>

</template>
