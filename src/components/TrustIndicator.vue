<template>
  <div class="trust-indicator-container text-center">
    <div
      class="indicator-circle m-auto"
      :class="{ 'bg-green-400': trustLevel === 'high', 'bg-yellow-400': trustLevel === 'medium', 'bg-red-400': trustLevel === 'low' }"
    ></div>
    <p class="mt-2">Trust Level: {{ trustLevel }}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'TrustIndicator',
  setup() {
    const trustLevel = ref<'high' | 'medium' | 'low'>('medium');

    return {
      trustLevel,
    };
  },
});
</script>

<style scoped>
.indicator-circle {
  width: 50px;
  height: 50px;
  border-radius: 50%;
}
</style>
