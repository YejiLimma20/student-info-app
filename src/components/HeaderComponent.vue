<template>
  <header class="sidebar-header">
    <div class="sidebar-inner">
      <div class="logo">
        <router-link to="/" class="logo-link">
          <span class="logo-icon-wrap">
            <svg class="logo-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="28" height="28">
              <path d="M12 3L1 9l11 6 9-4.91V17h2V9L12 3z"/>
              <path d="M5 13.18v4L12 21l7-3.82v-4L12 17l-7-3.82z"/>
            </svg>
          </span>
          <span class="logo-text">Student Info</span>
        </router-link>
      </div>
      <nav class="nav">
        <router-link to="/" class="nav-link">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
            <path d="M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z"/>
          </svg>
          <span>Home</span>
        </router-link>
        <router-link to="/students" class="nav-link">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
            <path d="M16 11c1.66 0 2.99-1.34 2.99-3S17.66 5 16 5c-1.66 0-3 1.34-3 3s1.34 3 3 3zm-8 0c1.66 0 2.99-1.34 2.99-3S9.66 5 8 5C6.34 5 5 6.34 5 8s1.34 3 3 3zm0 2c-2.33 0-7 1.17-7 3.5V19h14v-2.5c0-2.33-4.67-3.5-7-3.5zm8 0c-.29 0-.62.02-.97.05 1.16.84 1.97 1.97 1.97 3.45V19h6v-2.5c0-2.33-4.67-3.5-7-3.5z"/>
          </svg>
          <span>Students</span>
        </router-link>
        <router-link to="/about" class="nav-link">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 15h-2v-6h2v6zm0-8h-2V7h2v2z"/>
          </svg>
          <span>About</span>
        </router-link>
        <router-link to="/contact" class="nav-link">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
            <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
          </svg>
          <span>Contact</span>
        </router-link>
      </nav>
    </div>
  </header>
</template>

<script setup>
</script>

<style scoped>
.sidebar-header {
  height: 100%;
  background: linear-gradient(180deg, var(--mint-dark) 0%, var(--mint-primary) 100%);
  color: white;
  box-shadow: 4px 0 24px var(--mint-shadow);
}

.sidebar-inner {
  padding: 28px 20px;
  display: flex;
  flex-direction: column;
  gap: 32px;
  min-height: 100%;
}

.logo-link {
  display: flex;
  align-items: center;
  gap: 14px;
  padding: 8px 0;
}

.logo-icon-wrap {
  width: 44px;
  height: 44px;
  border-radius: 12px;
  background: rgba(255, 255, 255, 0.15);
  display: flex;
  align-items: center;
  justify-content: center;
}

.logo-icon {
  color: white;
}

.logo-text {
  font-weight: 700;
  font-size: 1.2rem;
  letter-spacing: -0.02em;
  color: white;
}

.nav {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.nav-link {
  color: rgba(255, 255, 255, 0.85);
  padding: 12px 16px;
  border-radius: 10px;
  transition: background 0.2s ease, color 0.2s ease;
  display: flex;
  align-items: center;
  gap: 12px;
  font-weight: 500;
}

.nav-link:hover {
  background: rgba(255, 255, 255, 0.12);
  color: white;
}

.nav-link.router-link-active {
  background: var(--mint-light);
  color: var(--mint-dark);
}
</style>
