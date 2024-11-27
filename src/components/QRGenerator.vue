<script setup lang="ts">
import { ref } from 'vue';
import QRCode from 'qrcode';

defineProps<{ msg: string }>();
const qrText = ref('');
function qrGenerate() {
  var canvas = document.getElementById('canvas');
  if (qrText.value == '') {
    qrText.value = 'sample';
  }
  QRCode.toCanvas(canvas, qrText.value, function (error) {
    if (error) console.error(error);
    console.log('success!');
  });
}
</script>

<template>
  <h1>{{ msg }}</h1>
  <div>
    <canvas
      id="canvas"
      width="100"
      height="100"
      style="border: 1px solid grey"
    ></canvas>
  </div>
  <p class="left">Text to convert: {{ qrText }}</p>
  <div><input v-model="qrText" placeholder="Edit me" /></div>
  <div><button @click="qrGenerate">QR Generate</button></div>
</template>

<style scoped>
.left {
  text-align: left;
  width: 300px;
  overflow-wrap: break-word;
}
button {
  background-color: #555555;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
}
</style>
