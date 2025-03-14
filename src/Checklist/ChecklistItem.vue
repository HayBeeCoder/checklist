<script lang="js" setup>
defineProps(["item"])
</script>

<template>
  <input type="checkbox" />
</template>

<style scoped>
input[type='checkbox'] {
  width: 32px;
  height: 32px;
  border-radius: 4px;
  background: purple;
  -webkit-appearance: none;
  appearance: none;
  -moz-appearance: none;
}
</style>
