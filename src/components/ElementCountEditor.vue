<template>
  <Card>
    <div class="flex-col gap-1">
      <h3>Elements</h3>

      <hr class="w-full" />

      <div class="flex-row gap-1 w-full">
        <label for="elementCount">Elements</label>
        <input
          class="flex-1"
          v-model="elementValue"
          id="elementCount"
          type="number"
          min="0"
          max="50"
        />
      </div>
    </div>
  </Card>
</template>

<script lang="ts" setup>
import Card from './Card.vue'
import { useVModel } from '@vueuse/core'

const props = defineProps<{
  modelValue: number
}>()

const elementValue = useVModel(props, 'modelValue')
</script>
