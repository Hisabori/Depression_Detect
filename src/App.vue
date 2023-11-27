<template>
  <div id="app">
    <h1>우울증 탐지기</h1>
    <textarea v-model="inputText" placeholder="여기에 텍스트를 입력하세요"></textarea>
    <button @click="analyzeText">분석하기</button>
    <p v-if="result">결과: {{ result }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'App',
  data() {
    return {
      inputText: '',
      result: null
    };
  },
  methods: {
    async analyzeText() {
      try {
        const response = await axios.post('http://localhost:3000/analyze', { text: this.inputText });
        this.result = response.data;
      } catch (error) {
        console.error('에러 발생:', error);
        this.result = '분석 중 에러가 발생했습니다.';
      }
    }
  }
};
</script>

<style>
/* 스타일은 여기에 추가 */
textarea {
  width: 100%;
  height: 100px;
}
button {
  margin-top: 10px;
}
</style>

