<template>
  <Card class="display">
    <div class="flex-col gap-1">
      <h3>Result</h3>

      <hr class="w-full" />

      <p v-if="displayType === 'block' || displayType === 'inline'">
        The quick brown fox <span class="text-child">jumps</span>
        <span class="text-child">over</span> the lazy dog
      </p>

      <div v-else class="display-box">
        <div class="child-box" v-for="index of [1, 2, 3, 4, 5]" :key="index">
          <p>Child {{ index }}</p>
        </div>
      </div>
    </div>
  </Card>
</template>

<script lang="ts" setup>
import Card from './Card.vue'
import { DisplayTypes } from './DisplaySelector.vue'

defineProps<{
  displayType: DisplayTypes
}>()
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

.display-box {
  display: v-bind(displayType);
}

.child-box {
  width: 100px;
  height: 100px;
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
</style>
