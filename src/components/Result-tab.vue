<template>
  <div class="result-tab">
    <h2>Reaction Result: {{ score }} ms</h2>
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      message: "",
    };
  },

  mounted() {
    if (this.score < 200) {
      this.message = "You are a ninja!";
    } else if (this.score < 300) {
      this.message = "You are a samurai!";
    } else if (this.score < 400) {
      this.message = "You are a warrior!";
    } else {
      this.message = "You are a grasshopper!";
    }
  },
};
</script>

<style>
.result-tab {
  width: 300px;
  padding: 30px 20px;
  margin: 40px auto;
  border-radius: 20px;
  background: black;
  color: white;
  align-items: center;
}
p {
  color: white;
}
</style>
