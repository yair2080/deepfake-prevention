<template>
  <div class="app-container">
    <header class="bg-blue-500 p-4 text-white text-center">
      <h1>Deepfake Prevention Tool</h1>
    </header>
    <main class="p-4">
      <DragDropUpload />
      <TrustIndicator />
    </main>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import DragDropUpload from './components/DragDropUpload.vue';
import TrustIndicator from './components/TrustIndicator.vue';

export default defineComponent({
  name: 'App',
  components: {
    DragDropUpload,
    TrustIndicator,
  },
});
</script>

<style>
body {
  font-family: 'Arial', sans-serif;
  margin: 0;
  padding: 0;
}
</style>
