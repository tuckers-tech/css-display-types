<template>
  <Card>
    <div class="flex-col gap-1">
      <h3>Justify (main axis)</h3>

      <hr class="w-full" />

      <div class="flex-col gap-2">
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="justify-flex-start"
            value="flex-start"
            v-model="pickedJustify"
          />
          <label for="justify-flex-start">Start</label>
        </div>
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="justify-center"
            value="center"
            v-model="pickedJustify"
          />
          <label for="justify-center">Center</label>
        </div>
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="justify-flex-end"
            value="flex-end"
            v-model="pickedJustify"
          />
          <label for="justify-flex-end">End</label>
        </div>
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="space-between"
            value="space-between"
            v-model="pickedJustify"
          />
          <label for="space-between">Space Between</label>
        </div>
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="space-around"
            value="space-around"
            v-model="pickedJustify"
          />
          <label for="space-around">Space Around</label>
        </div>
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="space-evenly"
            value="space-evenly"
            v-model="pickedJustify"
          />
          <label for="space-evenly">Space Evenly</label>
        </div>
      </div>
    </div>
  </Card>
</template>

<script lang="ts" setup>
import { useVModel } from '@vueuse/core'
import Card from './Card.vue'

export type JustifyType =
  | 'flex-start'
  | 'flex-end'
  | 'flex-center'
  | 'space-between'
  | 'space-around'
  | 'space-evenly'

const props = defineProps<{
  modelValue: JustifyType
}>()

const pickedJustify = useVModel(props, 'modelValue')
</script>
