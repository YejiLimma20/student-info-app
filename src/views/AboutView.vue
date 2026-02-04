<template>
  <div class="about-page">
    <header class="page-header">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="48" height="48">
        <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 15h-2v-6h2v6zm0-8h-2V7h2v2z"/>
      </svg>
      <h1>About Us</h1>
      <p>Learn more about the Student Information System</p>
    </header>

    <section class="about-content">
      <div class="about-card">
        <div class="about-icon">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="48" height="48">
            <path d="M12 3L1 9l11 6 9-4.91V17h2V9L12 3z"/>
            <path d="M5 13.18v4L12 21l7-3.82v-4L12 17l-7-3.82z"/>
          </svg>
        </div>
        <h2>Our Mission</h2>
        <p>
          The Student Information System is designed to streamline the management of student data
          for educational institutions. We provide a centralized platform that enables efficient
          tracking of student information, academic progress, and institutional resources.
        </p>
      </div>

      <div class="about-card">
        <div class="about-icon">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="48" height="48">
            <path d="M19 3h-4.18C14.4 1.84 13.3 1 12 1c-1.3 0-2.4.84-2.82 2H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm-7 0c.55 0 1 .45 1 1s-.45 1-1 1-1-.45-1-1 .45-1 1-1zm2 14H7v-2h7v2zm3-4H7v-2h10v2zm0-4H7V7h10v2z"/>
          </svg>
        </div>
        <h2>Key Features</h2>
        <ul class="features-list">
          <li>
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
              <path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z"/>
            </svg>
            Comprehensive student data management
          </li>
          <li>
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
              <path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z"/>
            </svg>
            Advanced search and filtering capabilities
          </li>
          <li>
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
              <path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z"/>
            </svg>
            Real-time data updates and synchronization
          </li>
          <li>
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
              <path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z"/>
            </svg>
            Secure API integration with external systems
          </li>
          <li>
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
              <path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z"/>
            </svg>
            User-friendly interface with responsive design
          </li>
        </ul>
      </div>

      <div class="about-card">
        <div class="about-icon">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="48" height="48">
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
          </svg>
        </div>
        <h2>Why Choose Us</h2>
        <p>
          Our system is built with modern technologies ensuring scalability, security, and performance.
          We prioritize user experience and continuously improve our platform based on feedback
          from educational institutions worldwide.
        </p>
      </div>
    </section>

    <section class="tech-stack">
      <h2>Technology Stack</h2>
      <div class="tech-grid">
        <div class="tech-item">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="32" height="32">
            <path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/>
          </svg>
          <span>Vue.js</span>
        </div>
        <div class="tech-item">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="32" height="32">
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.95-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93zm6.9-2.54c-.26-.81-1-1.39-1.9-1.39h-1v-3c0-.55-.45-1-1-1H8v-2h2c.55 0 1-.45 1-1V7h2c1.1 0 2-.9 2-2v-.41c2.93 1.19 5 4.06 5 7.41 0 2.08-.8 3.97-2.1 5.39z"/>
          </svg>
          <span>Vite</span>
        </div>
        <div class="tech-item">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="32" height="32">
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.95-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93z"/>
          </svg>
          <span>REST API</span>
        </div>
        <div class="tech-item">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="32" height="32">
            <path d="M20 6h-4V4c0-1.11-.89-2-2-2h-4c-1.11 0-2 .89-2 2v2H4c-1.11 0-1.99.89-1.99 2L2 19c0 1.11.89 2 2 2h16c1.11 0 2-.89 2-2V8c0-1.11-.89-2-2-2zm-6 0h-4V4h4v2z"/>
          </svg>
          <span>CSS3</span>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
// About page logic
</script>

<style scoped>
.about-page {
  max-width: 1200px;
  margin: 0 auto;
}

/* ===== HEADER ===== */
.page-header {
  text-align: center;
  padding: 40px;
  background: linear-gradient(135deg, #6B8E23 0%, #8FBC8F 50%, #CDE6C3 100%);
  border-radius: 15px;
  margin-bottom: 40px;
  color: #F5F1E8;
}

.page-header svg {
  margin-bottom: 15px;
}

.page-header h1 {
  font-size: 2.5rem;
  margin-bottom: 10px;
}

.page-header p {
  font-size: 1.1rem;
  opacity: 0.95;
}

/* ===== CONTENT ===== */
.about-content {
  display: grid;
  gap: 30px;
  margin-bottom: 40px;
}

.about-card {
  background: linear-gradient(135deg, #F5F1E8 0%, #ECE5D8 100%);
  border-radius: 15px;
  padding: 30px;
  border: 1px solid #8FBC8F;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
}

.about-icon {
  color: #6B8E23;
  margin-bottom: 15px;
}

.about-card h2 {
  color: #4F6F52;
  margin-bottom: 15px;
  font-size: 1.5rem;
}

.about-card p {
  color: #5F7F63;
  line-height: 1.8;
}

/* ===== FEATURES ===== */
.features-list {
  list-style: none;
  padding: 0;
}

.features-list li {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 10px 0;
  color: #5F7F63;
  font-size: 1rem;
}

.features-list svg {
  color: #6B8E23;
  flex-shrink: 0;
}

/* ===== TECH STACK ===== */
.tech-stack {
  background: linear-gradient(135deg, #F5F1E8 0%, #ECE5D8 100%);
  border-radius: 15px;
  padding: 40px;
  text-align: center;
  border: 1px solid #8FBC8F;
}

.tech-stack h2 {
  color: #4F6F52;
  margin-bottom: 30px;
  font-size: 1.8rem;
}

.tech-grid {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 30px;
}

.tech-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  color: #5F7F63;
}

.tech-item svg {
  color: #6B8E23;
}

.tech-item span {
  font-weight: 500;
}

</style>
