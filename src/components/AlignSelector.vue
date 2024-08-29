<template>
  <div class="align-selector"></div>
</template>

<script lang="ts" setup>
import { useVModel } from '@vueuse/core'

export type DisplayTypes = 'center' | 'flex-start' | 'flex-end'

const props = defineProps<{
  modelValue: DisplayTypes
}>()

const pickedDisplay = useVModel(props, 'modelValue')
</script>
