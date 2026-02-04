<template>
  <div class="home">

    <!-- HERO / WELCOME -->
    <section class="hero">
      <div class="hero-overlay"></div>
      <div class="hero-content">
        <h1>Welcome!</h1>
        <p>Manage students and reports efficiently with one dashboard.</p>
        <div class="hero-buttons">
          <router-link to="/students" class="cta-button">View Students</router-link>
        </div>
      </div>
      <div class="hero-image">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="#F5F1E8" width="200" height="200">
          <path d="M12 3L1 9l11 6 9-4.91V17h2V9L12 3z"/>
          <path d="M5 13.18v4L12 21l7-3.82v-4L12 17l-7-3.82z"/>
        </svg>
      </div>
    </section>

    <!-- QUICK ACCESS CARDS -->
    <section class="portal-cards">
      <div class="card" v-for="card in navCards" :key="card.title">
        <div class="card-icon">{{ card.icon }}</div>
        <h3>{{ card.title }}</h3>
        <p>{{ card.description }}</p>
      </div>
    </section>

    <!-- ANNOUNCEMENTS -->
    <section class="announcements">
      <h2>Announcements</h2>
      <div class="announcement-cards">
        <div class="announcement-card" v-for="ann in announcements" :key="ann.id">
          <p class="date">{{ ann.date }}</p>
          <p>{{ ann.text }}</p>
        </div>
      </div>
    </section>

  </div>
</template>

<script setup>
import { ref } from 'vue'

const navCards = [
  { icon: '📚', title: 'Manage Students', description: 'Add, edit, or view student records' },
  { icon: '📊', title: 'Reports', description: 'Generate academic reports and analytics' },
  { icon: '🔔', title: 'Notifications', description: 'View announcements and updates' }
]

const announcements = [
  { id: 1, date: '2026-02-01', text: 'New semester registration starts next week.' },
  { id: 2, date: '2026-01-20', text: 'Maintenance scheduled on 2026-02-10.' },
  { id: 3, date: '2026-01-15', text: 'New courses added for Spring 2026.' }
]
</script>

<style scoped>
.home {
  max-width: 1200px;
  margin: auto;
  padding: 20px;
  font-family: 'Poppins', sans-serif;
}

/* HERO */
.hero {
  position: relative;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: linear-gradient(135deg, #6B8E23, #8FBC8F, #CDE6C3);
  border-radius: 36px 36px 0 0;
  padding: 60px 40px;
  overflow: hidden;
  color: #F5F1E8;
}

.hero-overlay {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.05);
  border-radius: 36px 36px 0 0;
  z-index: 0;
}

.hero-content {
  z-index: 1;
  max-width: 600px;
}

.hero-content h1 {
  font-size: 3rem;
  margin-bottom: 20px;
}

.hero-content p {
  font-size: 1.2rem;
  margin-bottom: 30px;
}

.hero-buttons .cta-button {
  background: #6B8E23;
  color: #F5F1E8;
  padding: 12px 30px;
  border-radius: 30px;
  font-weight: bold;
  margin-right: 15px;
  transition: all 0.3s;
}

.hero-buttons .cta-button:hover {
  background: #5F7F1F;
}

.hero-image svg {
  z-index: 1;
}

/* PORTAL CARDS */
.portal-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 25px;
  margin: 50px 0;
}

.card {
  background: #ffffff;
  border-radius: 20px;
  padding: 25px;
  text-align: center;
  border: 1px solid #8FBC8F;
  box-shadow: 0 8px 20px rgba(0,0,0,0.08);
  transition: transform 0.3s, box-shadow 0.3s;
  cursor: pointer;
}

.card:hover {
  transform: translateY(-10px);
  box-shadow: 0 12px 25px rgba(0,0,0,0.15);
}

.card-icon {
  font-size: 2.5rem;
  margin-bottom: 15px;
}

/* ANNOUNCEMENTS */
.announcements h2 {
  text-align: center;
  color: #4F6F52;
  margin-bottom: 25px;
}

.announcement-cards {
  display: flex;
  gap: 20px;
  overflow-x: auto;
  padding-bottom: 10px;
}

.announcement-card {
  min-width: 250px;
  background: #ECE5D8;
  border-radius: 16px;
  padding: 20px;
  flex-shrink: 0;
  box-shadow: 0 6px 15px rgba(0,0,0,0.05);
  transition: transform 0.2s;
}

.announcement-card:hover {
  transform: translateY(-5px);
}

.announcement-card .date {
  font-size: 0.85rem;
  color: #5F7F63;
  margin-bottom: 10px;
}
</style>
