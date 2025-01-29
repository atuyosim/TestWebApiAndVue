<template>
  <div id="app">
    <h1>Weather Information</h1>
    <p v-if="weather">Temperature: {{ weather.temperature }}°C</p>
    <p v-if="weather">Condition: {{ weather.condition }}</p>
    <p v-else>Loading...</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      weather: null, // 天気情報を保存するデータ
    };
  },
  mounted() {
    // バックエンド API にリクエストを送信
    axios
      //.get("http://localhost:5004/api/weather")
      .get(`${import.meta.env.VITE_API_BASE_URL}/api/weather`)
      .then((response) => {
        console.log(response.data);
        //this.weather = response.data; // API のレスポンスを保存
        this.weather = response.data; // API のレスポンスを保存
      })
      .catch((error) => {
        console.error("API Error:", error);
      });
  },
};
</script>

<style>
/* 必要に応じてスタイルを追加 */
</style>
