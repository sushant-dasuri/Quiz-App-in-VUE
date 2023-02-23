<script setup>
import Question from "../components/Question.vue";
import QuizHeader from "../components/QuizHeader.vue";
import {useRoute} from "vue-router";
import quizzes from "../data/quizzes.json";
import { ref, watch, computed } from "vue";

const route = useRoute();
const quizId = parseInt(route.params.id);
const quiz = quizzes.find(q => q.id === quizId);
const currentQuestionIndex = ref(0);
/* const questionStatus = ref(`${currentQuestionIndex.value}/${quiz.questions.length}`)

watch(() => currentQuestionIndex.value, () => {
   questionStatus.value =  `${currentQuestionIndex.value}/${quiz.questions.length}`
}) */

const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`);
const barPercentage = computed(() => `${currentQuestionIndex.value / quiz.questions.length * 100}%`);

</script>

<template>
    <QuizHeader
    :questionStatus="questionStatus"
    :barPercentage="barPercentage" />
    <div>
        <Question :question= "quiz.questions[currentQuestionIndex]" :quiz= "quiz" />
    </div>
    <button @click="currentQuestionIndex++">Next</button>
</template>
