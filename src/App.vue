<script setup>
import { ref } from "vue";
import Recorder from "./components/Recorder.vue"
import ButtonVue from "./components/Button.vue";

const recorderRef = ref();
const buttonRef = ref();

const on_switch = ev => {
  console.log(ev);
  if (!ev) {
    recorderRef.value.record_start();
  } else {
    recorderRef.value.record_end();
  }
}
const on_error = ev => {
  buttonRef.value.force_off();
}
</script>

<template>
  <ButtonVue @on_switch="on_switch" ref="buttonRef"></ButtonVue>
  <Recorder @on_error="on_error" ref="recorderRef"></Recorder>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
