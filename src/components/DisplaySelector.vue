<template>
  <Card class="controls">
    <div class="flex-col gap-1">
      <h3>Display Type</h3>

      <hr class="w-full" />

      <div class="flex-col gap-2">
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="block"
            value="block"
            v-model="pickedDisplay"
          />
          <label for="block">Block</label>
        </div>
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="inline"
            value="inline"
            v-model="pickedDisplay"
          />
          <label for="inline">Inline</label>
        </div>

        <div class="flex-row gap-2 align-center">
          <input type="radio" id="flex" value="flex" v-model="pickedDisplay" />
          <label for="flex">Flex</label>
        </div>

        <div class="flex-row gap-2 align-center">
          <input type="radio" id="grid" value="grid" v-model="pickedDisplay" />
          <label for="grid">Grid</label>
        </div>
      </div>
    </div>
  </Card>
</template>

<script lang="ts" setup>
import Card from './Card.vue'
import { useVModel } from '@vueuse/core'

export type DisplayTypes = 'block' | 'inline' | 'inline-block' | 'flex' | 'grid'

const props = defineProps<{
  modelValue: DisplayTypes
}>()

const pickedDisplay = useVModel(props, 'modelValue')
</script>

<style lang="scss" scoped>
.controls {
  width: 300px;
}
</style>
