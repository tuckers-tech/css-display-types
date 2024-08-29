<template>
  <div class="w-full h-full flex-row gap-2">
    <div class="app__sidebar flex-col gap-2">
      <DisplaySelector v-model="displayType" />

      <template v-if="displayType === 'flex'">
        <div class="flex-row gap-2">
          <ElementCountEditor class="flex-1" v-model="elementCount" />
          <RandomFactor class="flex-1" v-model="randomFactor" />
        </div>
        <GapEditor v-model="gap" />
        <FlexDirection v-model="flexDirection" />
        <div class="flex-row gap-2">
          <JustifySelector class="flex-1" v-model="justify" />
          <AlignSelector class="flex-1" v-model="align" />
        </div>
      </template>

      <template v-if="displayType === 'grid'">
        <div class="flex-row gap-2">
          <ElementCountEditor class="flex-1" v-model="elementCount" />
          <RandomFactor class="flex-1" v-model="randomFactor" />
        </div>
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
import RandomFactor from './components/RandomFactor.vue'
import ElementCountEditor from './components/ElementCountEditor.vue'
import AlignSelector, { AlignType } from './components/AlignSelector.vue'
import JustifySelector, { JustifyType } from './components/JustifySelector.vue'

const displayType = ref<DisplayTypes>('flow')
const elementCount = ref<number>(10)
const gap = ref<number>(2)

const flexDirection = ref<FlexDirection>('row')
const align = ref<AlignType>('flex-start')
const justify = ref<JustifyType>('flex-start')

const columnCount = ref<number>(2)

const randomFactor = ref(0)

const displayAgg = computed(() => {
  return {
    displayType: displayType.value,
    elementCount: elementCount.value,
    randomFactor: randomFactor.value,

    // Shared
    gap: gap.value,

    // Flex
    flexDirection: flexDirection.value,
    justify: justify.value,
    align: align.value,

    // Grid
    columnCount: columnCount.value,
  }
})
</script>

<style lang="scss" scoped>
.app {
  &__sidebar {
    width: 400px;
    flex-shrink: 0;
  }
}
</style>
