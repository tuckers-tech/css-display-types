<template>
  <div class="named-container flex-col gap-2">
    <div class="named-container__heading">
      <code>{{ '.' + label }}</code>
    </div>

    <div class="named-container__content">
      <slot />
    </div>
  </div>
</template>

<script lang="ts" setup>
defineProps<{ label: string }>()
</script>

<style lang="scss" scoped>
.named-container {
  border: 1px solid #eaeaea;
  border-radius: 6px;

  &__heading {
    padding: 4px;
  }

  &__content {
    border-top: 1px solid #eaeaea;
    padding: 8px;
  }
}
</style>
