<template>
  <div>
    <h2>우울증 자가 진단 테스트</h2>
    <form @submit.prevent="submitAnswers">
      <div v-for="(question, index) in questions" :key="index">
        <p>{{ question.text }}</p>
        <input type="radio" :name="'question' + index" value="0"> 전혀 아니다<br>
        <input type="radio" :name="'question' + index" value="1"> 가끔 그렇다<br>
        <input type="radio" :name="'question' + index" value="2"> 자주 그렇다<br>
        <input type="radio" :name="'question' + index" value="3"> 항상 그렇다<br>
      </div>
      <button type="submit">제출</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      questions: [
        { text: "최근 기분이 우울하거나 희망이 없다고 느꼈나요?" },
        { text: "최근 불안하거나 초조하다고 느꼈나요?" },
        // Add more questions as needed
      ]
    };
  },
  methods: {
    submitAnswers() {
      // Collect answers and send them to the server for analysis
      // For now, just log the answers to the console
      let answers = {};
      this.questions.forEach((question, index) => {
        answers[index] = document.querySelector(`input[name='question${index}']:checked`)?.value;
      });
      console.log(answers);
    }
  }
};
</script>

