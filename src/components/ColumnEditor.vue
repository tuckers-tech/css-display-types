<template>
  <Card>
    <div class="flex-col gap-1">
      <h3>Columns</h3>

      <hr class="w-full" />

      <div class="flex-row gap-1 w-full">
        <label for="gap">Columns</label>
        <input
          class="flex-1"
          v-model="columnCount"
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

const columnCount = useVModel(props, 'modelValue')
</script>
