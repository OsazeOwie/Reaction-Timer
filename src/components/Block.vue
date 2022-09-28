<template>
  <div class="blockContainer">
    <div
      class="block"
      v-show="showBlock"
      :style="[{ marginLeft: marginL + 'px' }, { marginTop: marginT + 'px' }]"
      @click="stopTimer"
    >
      click me
    </div>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
      marginL: null,
      marginT: null
    };
  },
  mounted() {
    setTimeout(() => {
      this.marginL = 10 + Math.random() * 100;
      this.marginT = 10 + Math.random() * 250;
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
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
.blockContainer {
  width: 200px;
  margin: 0 auto;
}
.block {
  width: 20%;
  text-align: center;
  padding: 35px 35px;
  color: white;
  background-color: seagreen;
  border-radius: 20px;
}
</style>