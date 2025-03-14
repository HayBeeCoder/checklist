<script lang="js" setup>
import ChecklistItem from './ChecklistItem.vue'

defineProps(['items'])
</script>

<template>
  <ul>
    <li v-for="(item, key) in items" :key="key">
      <ChecklistItem :item="item"/>
    </li>
  </ul>
</template>
