<script setup>
import { ref } from "vue";
import { invoke } from "@tauri-apps/api/core";

const content = ref("")

async function fetchData() {
  try {
    const result = await invoke('dump_content');
    content.value = result
  } catch (error) {
    console.error('Error', error);
  }
}
</script>

<template>
  <p> 启动 Vite Tauri </p>
  <textarea v-model="content" rows="5" cols="30"></textarea>
  <button @click="fetchData">get data</button>
</template>
