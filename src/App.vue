<template>
  <div id="app">
    <aside class="sidebar">
      <HeaderComponent />
    </aside>
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
}

.sidebar {
  width: 260px;
  min-height: 100vh;
  flex-shrink: 0;
  position: sticky;
  top: 0;
}

.main-content {
  flex: 1;
  padding: 32px 40px 48px;
  min-width: 0;
}

@media (max-width: 768px) {
  #app {
    flex-direction: column;
  }

  .sidebar {
    width: 100%;
    min-height: auto;
    position: relative;
  }

  .main-content {
    padding: 24px 20px 40px;
  }
}
</style>
