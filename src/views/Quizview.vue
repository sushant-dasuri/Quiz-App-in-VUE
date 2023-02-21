<script setup>
import Question from "../components/Question.vue";
import QuizHeader from "../components/QuizHeader.vue";
import {useRoute} from "vue-router";
import quizzes from "../data/quizzes.json";
import { ref } from "@vue/reactivity";

const route = useRoute();
const quizId = parseInt(route.params.id);
const quiz = quizzes.find(q => q.id === quizId);
const currentQuestionIndex = ref(0);

</script>

<template>
    <QuizHeader />
    <div>
        <Question :question= "quiz.questions[currentQuestionIndex]" :quiz= "quiz" />
    </div>
</template>
