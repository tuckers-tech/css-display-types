<template>
  <Card>
    <div class="flex-col gap-1">
      <h3>Gap</h3>

      <hr class="w-full" />

      <div class="flex-row gap-1 w-full">
        <label for="random-factor">Random Factor</label>
        <input
          class="flex-1"
          v-model="randomFactor"
          id="random-factor"
          type="number"
          min="0"
          max="200"
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

const randomFactor = useVModel(props, 'modelValue')
</script>
