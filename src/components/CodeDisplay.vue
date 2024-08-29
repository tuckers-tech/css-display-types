<template>
  <Card
    v-if="
      props.display.displayType === 'flex' ||
      props.display.displayType === 'grid'
    "
  >
    <div class="flex-col gap-1">
      <h3>CSS</h3>

      <hr class="w-full" />

      <pre v-if="props.display.displayType === 'flex'">{{ flexCode }}</pre>
      <pre v-else>{{ gridCode }}</pre>
    </div>
  </Card>
</template>

<script lang="ts" setup>
import Card from './Card.vue'
import { computed } from 'vue'
import { AlignType } from './AlignSelector.vue'
import { JustifyType } from './JustifySelector.vue'

const props = defineProps<{
  display: {
    displayType: DisplayTypes
    elementCount: number
    flexDirection: FlexDirection
    gap: number
    align: AlignType
    justify: JustifyType
    columnCount: number
  }
}>()

const flexCode = computed(() => {
  return `
// Raw CSS
.display-box {
  display: flex;
  flex: ${props.display.flexDirection};
  gap: ${props.display.gap * 4}px;
  justify-content: ${props.display.justify};
  align-items: ${props.display.align};
}

// Hermes class list
flex-${props.display.flexDirection.replace('column', 'col')}
gap-${props.display.gap}
justify-${props.display.justify.replace('flex-', '').replace('space-', '')}
align-${props.display.align.replace('flex-', '')}
  `
})

const gridCode = computed(() => {
  return `
// Raw CSS
.display-box {
  display: grid;
  gap: ${props.display.gap * 4}px;
  grid-template-columns: repeat(${props.display.columnCount}, 1fr);
}
  `
})
</script>

<style lang="scss" scoped>
pre {
  margin: 0;
}
</style>
