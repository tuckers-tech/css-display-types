<template>
  <Card>
    <div class="flex-col gap-1">
      <h3>Gap</h3>

      <hr class="w-full" />

      <div class="flex-row gap-1 w-full">
        <label for="gap">Gap</label>
        <input
          class="flex-1"
          v-model="gapValue"
          id="gap"
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

const gapValue = useVModel(props, 'modelValue')
</script>
