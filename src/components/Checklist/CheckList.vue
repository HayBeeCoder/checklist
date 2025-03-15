<script lang="js" setup>
import ChecklistItem from './ChecklistItem.vue'

const props = defineProps(['items','lastChecked'])

</script>

<template>
  <ul>
    <li v-for="(item, key) in items" :key="key" :class="{'positive': item.checked, 'cursor-not-allowed': lastChecked + 1 != item.position || lastChecked != item.position  }">
      <ChecklistItem :item="item" :position="item.position" :last-checked="lastChecked"/>
    </li>
  </ul>
</template>

<style scoped>
ul{
  font-size: 0.8rem;
 
  display:flex;
  flex-direction: column;
  gap: 20px;
  align-items: stretch;

}

li{
  width: 100%;
  font-size: inherit;
  /* padding: 8px; */
  /* background-color: pink; */
  /* border-radius: 8px; */
  /* overflow: hidden; */
  border-radius: 8px;

  background: linear-gradient(90deg, #000000 0%, #5f1710 100%);
 

}
li.positive{
  
  background: linear-gradient(90deg, #000000 0%, #003402 100%);
}

</style>
