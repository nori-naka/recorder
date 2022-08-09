<script setup>
import { ref } from "vue";
const emit = defineEmits(["on_error"])
const record_state = ref(false);
let mr = null;

const download = (chunks) => {
  const blob = new Blob(chunks, { type: "video/webm" });
  const url = URL.createObjectURL(blob);
  const a = document.createElement("a");
  document.body.appendChild(a)
  a.style = "display: none";
  a.href = url;
  a.download = "video.webm";
  a.click();
  window.URL.revokeObjectURL(url);
}

const record_start = async () => {
  const option = { mimeType: "video/webm; codecs=vp9" }
  const chunks = [];
  try {
    record_state.value = true;
    const stream = await navigator.mediaDevices.getDisplayMedia();
    mr = new MediaRecorder(stream, option);
    mr.ondataavailable = (ev) => {
      if (ev.data.size > 0) {
        chunks.push(ev.data);
        download(chunks);
      }
    }
    mr.onstop = (ev) => {
      const [ track ] = stream.getVideoTracks();
      track.stop();
    }
    mr.start();
  } catch (err) {
    console.log(err);
    record_end();
    emit("on_error", record_state.value);
  }
}
const record_end = () => {
  if (mr) mr.stop();
  record_state.value = false;
}

defineExpose({
  record_start, record_end
})

</script>
<template>
  <div></div>
  <!-- <div @click="record_start" :class="{ text_red: record_state }">{{ record_state ? "録画を開始しました": "録画開始" }}</div>
  <div @click="record_end">録画停止</div> -->
</template>

<style scoped>
.text_red {
  color: red;
}
</style>