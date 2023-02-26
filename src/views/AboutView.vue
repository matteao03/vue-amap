<template>
  <div class="container">
    <div class="item">
      <div class="title">1212</div>
      <div class="about" id="about1"></div>
    </div>
    <div class="item">
      <div class="title">2323</div>
      <div class="about" id="about2"></div>
    </div>
    <div class="item">
      <div class="title">3434</div>
      <div class="about" id="about3"></div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { onMounted } from 'vue'

onMounted(() => {})
</script>
<style>
.container {
  display: flex;
  height: 400px;
}
.title {
  padding: 10px;
}
.item {
  display: flex;
  flex: 1;
  flex-direction: column;
}
.about {
  flex: 1;
}
</style>
