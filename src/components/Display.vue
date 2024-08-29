<template>
  <Card class="display">
    <div class="flex-col gap-1">
      <h3>Result</h3>

      <hr class="w-full" />

      <p
        v-if="
          displayType === 'flow' ||
          displayType === 'block' ||
          displayType === 'inline'
        "
      >
        The quick brown fox <span class="text-child">jumps</span>
        <span class="text-child">over</span> the lazy dog
      </p>

      <NamedContainer v-else-if="displayType === 'flex'" label="display-box">
        <div class="display-box-flex">
          <NamedContainer
            label="child"
            class="child-box"
            v-for="index of childElements"
            :key="index"
          >
            <p>Child {{ index }}</p>
          </NamedContainer>
        </div>
      </NamedContainer>

      <NamedContainer v-else label="display-box">
        <div class="display-box-grid">
          <NamedContainer
            label="child"
            class="child-box"
            v-for="index of childElements"
            :key="index"
          >
            <p>Child {{ index }}</p>
          </NamedContainer>
        </div>
      </NamedContainer>
    </div>
  </Card>
</template>

<script lang="ts" setup>
import Card from './Card.vue'
import { DisplayTypes } from './DisplaySelector.vue'
import { FlexDirection } from './FlexDirection.vue'
import { computed } from 'vue'
import NamedContainer from './NamedContainer.vue'

const props = defineProps<{
  display: {
    displayType: DisplayTypes
    elementCount: number
    flexDirection: FlexDirection
    gap: number
    columnCount: number
  }
}>()

const childElements = computed(() =>
  Array.apply(null, Array(props.display.elementCount)).map(function (y, i) {
    return i
  }),
)

const displayType = computed(() => props.display.displayType)

const gap = computed(() => `${props.display.gap * 4}px`)
const flexDirection = computed(() => props.display.flexDirection)
const columnCount = computed(() => props.display.columnCount)
const rowCount = computed(() => props.display.rowCount)
</script>

<style lang="scss" scoped>
.display {
  flex: 1;
}

.text-child {
  display: v-bind(displayType);
  border-radius: 6px;
  padding: 8px;
  border: 1px solid #00a351;
  background: linear-gradient(
      0deg,
      rgba(#00a351, 0.08) 0%,
      rgba(#00a351, 0.08) 100%
    ),
    #fff;
  color: #00a351;
}

.display-box-flex {
  display: v-bind(displayType);
  gap: v-bind(gap);
  flex-direction: v-bind(flexDirection);
  flex-wrap: wrap;
}

.display-box-grid {
  display: v-bind(displayType);
  gap: v-bind(gap);
  grid-template-columns: repeat(v-bind(columnCount), 1fr);
}

.child-box {
  border-radius: 4px;
  padding: 8px;
  border: 1px solid #00a351;
  background: linear-gradient(
      0deg,
      rgba(#00a351, 0.08) 0%,
      rgba(#00a351, 0.08) 100%
    ),
    #fff;
  color: #00a351;
}
</style>
