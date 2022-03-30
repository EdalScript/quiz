<template>
  <div class="container">
    <Questions
      v-if="questionsAnswered < questions.length"
      :questions="questions"
      :questionsAnswered="questionsAnswered"
      @question-answered="questionAnswered"
    />
    <Result v-else />
    <button type="button" class="reset-btn">Reset</button>
  </div>
</template>

<script>
import Questions from "./components/Questions.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: {
    Questions,
    Result,
  },
  data() {
    return {
      questionsAnswered: 0,
      totalCorrect: 0,
      questions: [
        {
          q: "Sample question",
          answers: [
            {
              text: "1",
              is_correct: true,
            },
            {
              text: "11",
              is_correct: false,
            },
            {
              text: "111",
              is_correct: false,
            },
            {
              text: "1111",
              is_correct: false,
            },
          ],
        },
        {
          q: 'Sample question 2',
          answers: [
            {
              text: "1",
              is_correct: false,
            },
            {
              text: "11",
              is_correct: false,
            },
            {
              text: "111",
              is_correct: true,
            },
            {
              text: "1111",
              is_correct: false,
            },
          ],
        },
        {
          q: "Sample question 3",
          answers: [
            {
              text: "1",
              is_correct: false,
            },
            {
              text: "11",
              is_correct: true,
            },
            {
              text: "111",
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!",
        },
        {
          min: 3,
          max: 3,
          title: "Wow, you're a genius!",
          desc: "Studying has definitely paid off for you!",
        },
      ],
    };
  },
  methods: {
    questionAnswered(is_correct) {
      if (is_correct) {
        this.totalCorrect++;
      }
      this.questionsAnswered++;
    },
    reset() {
      this.questionsAnswered = 0;
      this.totalCorrect = 0;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
