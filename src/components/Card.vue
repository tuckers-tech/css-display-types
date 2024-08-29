<template>
  <div class="card">
    <slot />
  </div>
</template>

<style scoped>
.card {
  padding: 12px;
  background-color: #ffffff;

  border: 1px solid #eaeaea;
  border-radius: 8px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.15);
}
</style>
