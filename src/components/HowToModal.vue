<template>
  <div class="backdrop" @click.self="closeModal">
    <ol class="modal">
      <h3>How To Play</h3>
      <p>click the "start" button to begin</p>
      <p>a box will appear at a random time</p>
      <p>click/tap the box as fast as you can.</p>
      <p :style="{fontWeight: 600}">GoodLuck!</p>
    </ol>
  </div>
</template>

<script>
export default {
  props: ['howTo'],
  methods: {
    closeModal() {
      this.$emit("close")
    }
  }
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgb(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
.modal {
  width: 20rem;
  padding: 1em;
  margin: 100px auto;
  background: seagreen;
  color: white;
  border-radius: 10px;
}
.modal h3 {
  text-decoration: underline;
}
</style>