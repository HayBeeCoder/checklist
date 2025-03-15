<script lang="js" setup>
const props = defineProps(['item', 'lastChecked'])
// console.log({prp: props.item.checked})
</script>

<template>
  <label
    :for="item.value"
    :class="{
      positive: item.checked,
      'cursor-not-allowed': lastChecked + 1 != item.position || lastChecked != item.position,
    }"
  >
    <span>
      <input
        type="checkbox"
        v-model="item.checked"
        :id="item.value"
        :disabled="item.checked ? lastChecked != item.position : lastChecked + 1 != item.position"
      />

      <!-- <input type="checkbox" name="item.position" /> -->
    </span>
    <span class="text gradient-text">{{ item.value }}</span>
  </label>
</template>

<style scoped>
label {
  cursor: pointer;
  display: inline-block;
  width: 100%;
  display: inline-flex;
  gap: 20px;
  align-items: center;
  min-width: 300px;
  padding: 0.8rem 0rem;
  padding-left: 1rem;
  border: 2px solid rgba(255, 102, 102, 0.2);
  
  border-radius: 8px;

  box-shadow: 0px 8px 4.9px 0px rgba(0, 0, 0, 0.97);
  transition: all ease-in-out 1000;
}

label.positive {
  border: 2px solid rgba(79, 150, 81, 0.2);

}
span {
  display: inline-block;
  line-height: 1rem;
}

input[type='checkbox'] {
  display: inline-block;
  position: relative;
  width: 21px;
  height: 21px;
  border-radius: 4px;
  background: linear-gradient(257.72deg, #ffffff -59.59%, #606060 243.09%, #000000 335.67%);

  -webkit-appearance: none;
  appearance: none;
  -moz-appearance: none;
  border: 0.5px solid;

  border-image-source: linear-gradient(180deg, #000000 0%, #464646 100%);
}

input[type='checkbox']:checked {
  background: linear-gradient(257.72deg, #00ff09 -59.59%, #606060 243.09%, #000000 335.67%);
}

input[type='checkbox'].positive {
  /* background:; */
}

span.text {
  background-image: linear-gradient(88.03deg, #939393 0.71%, #afafaf 43.39%, #e6e6e6 95.56%);
}
</style>
