<template>
  <div class="w-full h-full flex-row gap-2">
    <div class="app__sidebar flex-col gap-2">
      <DisplaySelector v-model="displayType" />

      <template v-if="displayType === 'flex'">
        <FlexDirection v-model="flexDirection" />
        <GapEditor v-model="gap" />
      </template>

      <template v-if="displayType === 'grid'">
        <GapEditor v-model="gap" />
        <ColumnEditor v-model="columnCount" />
      </template>
    </div>

    <Display :display="displayAgg" />

    <CodeDisplay class="app__sidebar" :display="displayAgg" />
  </div>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue'

import DisplaySelector, { DisplayTypes } from './components/DisplaySelector.vue'
import Display from './components/Display.vue'
import FlexDirection from './components/FlexDirection.vue'
import GapEditor from './components/GapEditor.vue'
import CodeDisplay from './components/CodeDisplay.vue'
import ColumnEditor from './components/ColumnEditor.vue'

const displayType = ref<DisplayTypes>('flow')

const flexDirection = ref<FlexDirection>('row')
const gap = ref<number>(2)

const elementCount = ref<number>(20)

const columnCount = ref<number>(2)

const displayAgg = computed(() => {
  return {
    displayType: displayType.value,
    elementCount: elementCount.value,

    // Shared
    gap: gap.value,

    // Flex
    flexDirection: flexDirection.value,

    // Grid
    columnCount: columnCount.value,
  }
})
</script>

<style lang="scss" scoped>
.app {
  &__sidebar {
    width: 300px;
    flex-shrink: 0;
  }
}
</style>
