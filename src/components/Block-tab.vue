<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>
<script>
export default {
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  props: ["delay"],
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("reaction", this.reactionTime);
      console.log(this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 300px;
  padding: 100px 0;
  margin: 40px auto;
  background-color: rgb(237, 138, 18);
  border-radius: 20px;
  color: #fff;
  align-items: center;
  font-size: 24px;
  cursor: pointer;
}
</style>
