<template>
  <Card>
    <div class="flex-col gap-1">
      <h3>Align (cross axis)</h3>

      <hr class="w-full" />

      <div class="flex-col gap-2">
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="flex-start"
            value="flex-start"
            v-model="pickedAlign"
          />
          <label for="flex-start">Start</label>
        </div>
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="center"
            value="center"
            v-model="pickedAlign"
          />
          <label for="center">Center</label>
        </div>
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="flex-end"
            value="flex-end"
            v-model="pickedAlign"
          />
          <label for="flex-end">End</label>
        </div>
      </div>
    </div>
  </Card>
</template>

<script lang="ts" setup>
import { useVModel } from '@vueuse/core'
import Card from './Card.vue'

export type AlignType = 'center' | 'flex-start' | 'flex-end'

const props = defineProps<{
  modelValue: AlignType
}>()

const pickedAlign = useVModel(props, 'modelValue')
</script>
