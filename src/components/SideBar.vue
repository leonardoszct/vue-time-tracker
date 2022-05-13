<template>
  <header>
    <div class="logo">
      <i class="fa-solid fa-stopwatch"></i>
      <h1 class="is-size-4">Time Tracker</h1>
    </div>
  </header>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "SideBar",
});
</script>

<style scoped>
header {
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  color: white;
}

header .logo {
  text-align: center;
  padding: 1rem;
}

header .logo i {
  font-size: 3rem;
  margin-bottom: 1rem;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>