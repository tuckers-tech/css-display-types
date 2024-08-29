<template>
  <Card>
    <div class="flex-col gap-1">
      <h3>Flex Direction</h3>

      <hr class="w-full" />

      <div class="flex-col gap-1">
        <div class="flex-row gap-2 align-center">
          <input type="radio" id="row" value="row" v-model="pickedDirection" />
          <label for="row">Row</label>
        </div>
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="column"
            value="column"
            v-model="pickedDirection"
          />
          <label for="column">Column</label>
        </div>
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="row-reverse"
            value="row-reverse"
            v-model="pickedDirection"
          />
          <label for="row-reverse">Row Reverse</label>
        </div>
        <div class="flex-row gap-2 align-center">
          <input
            type="radio"
            id="column-reverse"
            value="column-reverse"
            v-model="pickedDirection"
          />
          <label for="column-reverse">Column Reverse</label>
        </div>
      </div>
    </div>
  </Card>
</template>

<script lang="ts" setup>
import Card from './Card.vue'
import { Ref } from 'vue'
import { useVModel } from '@vueuse/core'

export interface FlexOptions {
  flexDirection: Ref<'row' | 'column' | 'row-reverse' | 'column-reverse'>
  gap: Ref<number>
}

export type FlexDirection = 'row' | 'column' | 'row-reverse' | 'column-reverse'

const props = defineProps<{
  modelValue: FlexDirection
}>()

const pickedDirection = useVModel(props, 'modelValue')
</script>
