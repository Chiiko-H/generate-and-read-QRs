<script setup lang="ts">
import { ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue';
import QRGenerator from './components/QRGenerator.vue';
import QRReader from './components/QRReader.vue';

const currentComp = ref(QRGenerator);
const currentCompName = ref('QRGenerator');
const selectIdx = ref('0');
const compList = [QRGenerator, QRReader];
const compNameList: string[] = ['QRGenerator', 'QRReader'];
function switchComp() {
  console.log(selectIdx.value);
  var idx = parseInt(selectIdx.value);
  currentComp.value = compList[idx];
  currentCompName = compNameList[idx];
}
</script>

<template>
  <input type="radio" value="0" v-model="selectIdx" @change="switchComp" />
  <label for="QRGenerator">QRGenerator</label>

  <input type="radio" value="1" v-model="selectIdx" @change="switchComp" />
  <label for="QRReader">QRReader</label>
  <hr />
  <h4>{{ currentCompName }}</h4>
  <component :is="currentComp" />
</template>

<style scoped>
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
