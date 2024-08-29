<template>
  <div class="w-full h-full flex-row gap-2">
    <div class="flex-col gap-2">
      <DisplaySelector v-model="displayType" />
    </div>

    <Display :display-type="displayType" />
  </div>
</template>

<script setup lang="ts">
import DisplaySelector, { DisplayTypes } from './components/DisplaySelector.vue'
import Display from './components/Display.vue'
import { ref } from 'vue'

const displayType = ref<DisplayTypes>('block')
</script>
