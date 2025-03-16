<script setup>
import { computed, onMounted, ref, watch } from 'vue'
import CheckList from './components/Checklist/CheckList.vue'
import useLocalStorage from './composables/useLocalStorage'

const items = ref([
  {
    value: 'Has Asian session ended?',
    checked: false,
    position: 0,
  },
  {
    value: 'Identified potential Medium inducement zone?',
    checked: false,
    position: 1,
  },
  {
    value: 'Have you identified potential POI’s?',
    checked: false,
    position: 2,
  },
  {
    value: 'Identified direction of LQ being created?',
    checked: false,
    position: 3,
  },
  {
    value: 'Has Asian Range been induced?',
    checked: false,
    position: 4,
  },
  {
    value: 'Have you had a Medium inducement?',
    checked: false,
    position: 5,
  },
  {
    value: 'Do you have a rBOS away from the inducement? ',
    checked: false,
    position: 6,
  },
  {
    value: 'Do you have a valid target?',
    checked: false,
    position: 7,
  },
  {
    value: 'Do you have a general structural incucement?',
    checked: false,
    position: 8,
  },
])

const { read, write } = useLocalStorage('checklist', 'items')
// const checked = ref(-1)
const checked = computed(() => {
  return items.value.filter((item) => item.checked).length
})

onMounted(() => {
  const itemsFromLocal = read()
  if (itemsFromLocal == null) {
    return
  } else {
    items.value = itemsFromLocal
  }
})

watch(items, (newItems) => {

  
  
  write(newItems)
},{
  deep: true
})
</script>

<template>
  <div
    :class="{
      'ellipse upper-right-ellipse': true,
      positive: checked >= 6,
      negative: checked < 6,
    }"
    aria-hidden
  ></div>
  <div class="ellipse lower-left-ellipse" aria-hidden></div>
  <header class="">
    <!-- <div class="masked-bg"> -->
    <h1 class="gradient-text masked-bg irish-grover">CheckList</h1>
    <!-- </div> -->
  </header>

  <main>
    <CheckList :items="items" :checked="checked" />
    <div class="progress-wrapper" aria-hidden>
      <div
        class="progress"
        aria-hidden
        :style="{ width: `${((checked ) * 100) / items.length}%` }"
      ></div>
      <p class="irish-grover progress-value">
        {{ Math.floor(((checked ) * 100) / items.length) }}%
      </p>
    </div>
  </main>
</template>

<style scoped>
.masked-bg {
  background-image: linear-gradient(88.03deg, #ffffff 0.71%, #ffd6d1 95.56%);
}

.masked-bg.positive {
  background-image: linear-gradient(88.03deg, #ffffff 0.71%, #bfe0c1 95.56%);
}
h1 {
  font-size: 2rem;
  text-align: center;
}

main {
  position: relative;
  z-index: 1000;
  padding-bottom: 2rem;
  width: 94vw;
  max-width: 400px;
  margin: 0 auto;
}
header {
  padding: 2rem;
  text-align: center;
  display: flex;
  justify-content: space-around;
}
.ellipse {
  position: fixed;
  width: 24rem;
  height: 24rem;
  border-radius: 100%;
  filter: blur(15rem);
  z-index: -100px;
}

.upper-right-ellipse {
  transform: translateX(-40%);
  top: 21px;
  left: 100%;
  position: fixed;
  top: 0;
  left: 100%;
}
.upper-right-ellipse.negative {
  z-index: -100px;
  filter: blur(15rem);
  background-color: rgba(232, 41, 22, 1);
}
.upper-right-ellipse.positive {
  z-index: -100px;
  filter: blur(15rem);
  background-color: rgba(0, 255, 9, 1);
}

.lower-left-ellipse {
  background: rgba(37, 37, 37, 1);
  left: 0;
  bottom: 21px;
  transform: translateX(-50%);
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

.progress-wrapper {
  margin: 20px 0 20px;
  display: block;
  width: 100%;
  height: 10px;
  border-radius: 28px;
  background: linear-gradient(90deg, #000000 0%, #252525 100%);
  border: 1px solid rgba(15, 15, 15, 1);
}

.progress {
  background: linear-gradient(90deg, #ff0000 0%, #ff7200 44.9%, #feea15 71.9%, #00ff09 100%);
  height: 100%;
  border-radius: 28px;
}

.progress-value {
  text-align: center;
  margin: 10px;
  color: rgba(188, 188, 188, 1);
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}

@media (min-width: 868px) {
  .ellipse {
    width: 42rem;
    height: 42rem;
  }
  .upper-right-ellipse {
    transform: translateX(-80%);
    top: -21%;
    /* filter: blur(rem); */
    /* left: 100%; */
    /* position: fixed; */
    /* background-color: rgba(232, 41, 22, 1); */
    /* top: 0; */
    /* left: 100%; */
  }
}
</style>
