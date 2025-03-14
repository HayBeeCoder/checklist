<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <div class="ellipse upper-right-ellipse" aria-hidden></div>
  <div class="ellipse lower-left-ellipse" aria-hidden></div>
  <header class="">
    <!-- <div class="masked-bg"> -->
    <h1 class="gradient-text masked-bg">CheckList</h1>
    <!-- </div> -->
  </header>

  <main>
    <CheckList />
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
  font-size: 4rem;
  text-align: center;
  
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
}

.upper-right-ellipse {
  transform: translateX(-40%);
  top: 21px;
  left: 100%;
  position: fixed;
  background-color: rgba(232, 41, 22, 1);
  top: 0;
  left: 100%;
}

.upper-right-ellipse.positive {
  background: rgba(0, 255, 9, 1);
}

.lower-left-ellipse {
  background: rgba(37, 37, 37, 1);
  bottom: 21px;
  transform: translateX(-60%);
}

.logo {
  display: block;
  margin: 0 auto 2rem;
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

@media (min-width: 868px){
  .ellipse{
    width: 42rem;
    height: 42rem;
  }
  .upper-right-ellipse {
  transform: translateX(-80%);
  top: -21px;
  filter: blur(25rem);
  /* left: 100%; */
  /* position: fixed; */
  /* background-color: rgba(232, 41, 22, 1); */
  /* top: 0; */
  /* left: 100%; */
}
}
</style>
