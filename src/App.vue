<script setup>
</script>

<template>
  <div>
    <header>
      <p>header</p>
    </header>

    <main>
      <Lista />
    </main>
  </div>
  
</template>

<script>
import Lista from "./components/Lista.vue";
export default {
  components : {
    Lista
  }
}
</script>

<style scoped>
header{
  
  min-height: 5vh;
  min-width: 100vw;
  background-color: rebeccapurple;
}
</style>
