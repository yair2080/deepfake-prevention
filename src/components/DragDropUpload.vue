<template>
  <div class="drag-drop-container">
    <div
      class="drag-drop-area border-dashed border-2 border-gray-400 p-6 rounded-md"
      @dragover.prevent
      @drop.prevent="handleDrop"
    >
      <p>Drag and drop your file here, or click to upload.</p>
      <input type="file" @change="handleFileUpload" class="hidden" ref="fileInput" />
    </div>
    <div v-if="file">
      <p class="mt-4">Uploaded File: {{ file.name }}</p>
    </div>
    <button
      class="bg-blue-500 text-white p-2 rounded mt-4"
      @click="processFile"
      :disabled="!file"
    >
      Process File
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'DragDropUpload',
  setup() {
    const file = ref<File | null>(null);

    const handleDrop = (event: DragEvent) => {
      if (event.dataTransfer?.files[0]) {
        file.value = event.dataTransfer.files[0];
      }
    };

    const handleFileUpload = (event: Event) => {
      const target = event.target as HTMLInputElement;
      if (target.files?.[0]) {
        file.value = target.files[0];
      }
    };

    const processFile = () => {
      if (file.value) {
        alert(`Processing: ${file.value.name}`);
        // Add backend API call or frontend validation logic here
      }
    };

    return {
      file,
      handleDrop,
      handleFileUpload,
      processFile,
    };
  },
});
</script>

<style scoped>
.drag-drop-area {
  cursor: pointer;
  text-align: center;
  background-color: #f9f9f9;
}
</style>
