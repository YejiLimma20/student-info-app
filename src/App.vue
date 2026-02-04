<template>
  <div id="app">
    <HeaderComponent />
    <main class="main-content">
      <router-view />
    </main>
  </div>
</template>

<script setup>
import HeaderComponent from './components/HeaderComponent.vue'
</script>

<style scoped>
#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.main-content {
  flex: 1;
  padding: 20px;
}
</style>
