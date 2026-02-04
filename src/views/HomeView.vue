<template>
  <div class="home">
    <section class="hero">
      <svg class="hero-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="60" height="60">
        <path d="M12 3L1 9l11 6 9-4.91V17h2V9L12 3z"/>
        <path d="M5 13.18v4L12 21l7-3.82v-4L12 17l-7-3.82z"/>
      </svg>
      <h1 class="hero-title">Student Information System</h1>
      <p class="hero-subtitle">
        Welcome to the Student Info App - Your centralized platform for managing student data
      </p>
    </section>

    <section class="features">
      <div class="feature-card">
        <div class="feature-icon">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="48" height="48">
            <path d="M19 3h-4.18C14.4 1.84 13.3 1 12 1c-1.3 0-2.4.84-2.82 2H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm-7 0c.55 0 1 .45 1 1s-.45 1-1 1-1-.45-1-1 .45-1 1-1zm2 14H7v-2h7v2zm3-4H7v-2h10v2zm0-4H7V7h10v2z"/>
          </svg>
        </div>
        <h3>Student Management</h3>
        <p>Easily add, edit, and manage student information with our intuitive interface.</p>
      </div>

      <div class="feature-card">
        <div class="feature-icon">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="48" height="48">
            <path d="M15.5 14h-.79l-.28-.27A6.471 6.471 0 0016 9.5 6.5 6.5 0 109.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/>
          </svg>
        </div>
        <h3>Quick Search</h3>
        <p>Find students instantly with our powerful search and filter capabilities.</p>
      </div>

      <div class="feature-card">
        <div class="feature-icon">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="48" height="48">
            <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
          </svg>
        </div>
        <h3>Data Overview</h3>
        <p>Get comprehensive views of student data and academic progress.</p>
      </div>

      <div class="feature-card">
        <div class="feature-icon">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="48" height="48">
            <path d="M4 6h18V4H4c-1.1 0-2 .9-2 2v11H0v3h14v-3H4V6zm19 2h-6c-.55 0-1 .45-1 1v10c0 .55.45 1 1 1h6c.55 0 1-.45 1-1V9c0-.55-.45-1-1-1zm-1 9h-4v-7h4v7z"/>
          </svg>
        </div>
        <h3>API Integration</h3>
        <p>Seamlessly connect with external systems through our REST API.</p>
      </div>
    </section>

    <section class="cta-section">
      <h2>Ready to get started?</h2>
      <p>Explore our student database and manage your institution's data efficiently.</p>
      <router-link to="/students" class="cta-button">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
          <path d="M16 11c1.66 0 2.99-1.34 2.99-3S17.66 5 16 5c-1.66 0-3 1.34-3 3s1.34 3 3 3zm-8 0c1.66 0 2.99-1.34 2.99-3S9.66 5 8 5C6.34 5 5 6.34 5 8s1.34 3 3 3zm0 2c-2.33 0-7 1.17-7 3.5V19h14v-2.5c0-2.33-4.67-3.5-7-3.5zm8 0c-.29 0-.62.02-.97.05 1.16.84 1.97 1.97 1.97 3.45V19h6v-2.5c0-2.33-4.67-3.5-7-3.5z"/>
        </svg>
        View All Students
      </router-link>
    </section>

    <section class="demo-section">
      <h2>Featured Students</h2>
      <p class="section-subtitle">Meet some of our outstanding students</p>
      
      <div class="demo-students">
        <StudentComponent
          v-for="student in featuredStudents"
          :key="student.id"
          :student="student"
          :student-name="student.name"
          :course="student.course"
          :year="student.year"
          :student-id="student.id"
          :email="student.email"
          :status="student.status"
          @view-details="handleViewDetails"
          @edit-student="handleEditStudent"
        />
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import StudentComponent from '../components/StudentComponent.vue'

// Featured students data
const featuredStudents = ref([
  { id: '2024001', name: 'Kharl Angelo Dumangas', course: 'Computer Science', year: 3, email: 'kharlangelo.dumangas@school.edu', status: 'Active' },
  { id: '2024002', name: 'Mark Anthony Dela Rosa', course: 'Information Technology', year: 2, email: 'markanthony.delarosa@school.edu', status: 'Active' },
  { id: '2024003', name: 'Andrei Asnan', course: 'Software Engineering', year: 4, email: 'andrei.asnan@school.edu', status: 'Active' },
  { id: '2024004', name: 'Jan Rhen Garcia', course: 'Data Science', year: 2, email: 'janrhen.garcia@school.edu', status: 'Active' },
  { id: '2024005', name: 'Juan Miguel Larios', course: 'Web Development', year: 1, email: 'juanmiguel.larios@school.edu', status: 'Active' },
  { id: '2024006', name: 'Jayvee Biñas', course: 'Cyber Security', year: 3, email: 'jayvee.binas@school.edu', status: 'Active' },
  { id: '2024007', name: 'Gio McGrey Calugas', course: 'Mobile Computing', year: 4, email: 'giomcgrey.calugas@school.edu', status: 'Active' },
  { id: '2024008', name: 'Kerwin James Macasunod', course: 'Computer Science', year: 2, email: 'kerwinjames.macasunod@school.edu', status: 'Active' },
  { id: '2024009', name: 'Kirk Franklin Macasunod', course: 'Information Technology', year: 1, email: 'kirkfranklin.macasunod@school.edu', status: 'Active' },
  { id: '2024010', name: 'Mandy Factolerin', course: 'Software Engineering', year: 3, email: 'mandy.factolerin@school.edu', status: 'Active' }
])

// Event handlers
const handleViewDetails = (student) => {
  console.log('View details for:', student)
  alert(`Viewing details for ${student.name}`)
}

const handleEditStudent = (student) => {
  console.log('Edit student:', student)
  alert(`Editing ${student.name}'s profile`)
}
</script>

<style scoped>
.home {
  max-width: 1200px;
  margin: 0 auto;
}

.hero {
  text-align: center;
  padding: 56px 24px;
  background: linear-gradient(145deg, var(--mint-dark) 0%, var(--mint-primary) 60%, var(--mint-mid) 100%);
  color: white;
  border-radius: 18px;
  margin-bottom: 40px;
  box-shadow: 0 8px 32px var(--mint-shadow);
}

.hero-icon {
  display: block;
  margin: 0 auto 20px;
}

.hero-title {
  font-size: 2.5rem;
  margin-bottom: 15px;
}

.hero-subtitle {
  font-size: 1.2rem;
  opacity: 0.9;
}

.features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  margin-bottom: 40px;
}

.feature-card {
  background: linear-gradient(145deg, var(--mint-white) 0%, var(--mint-bg) 100%);
  border-radius: 14px;
  padding: 28px;
  text-align: center;
  box-shadow: 0 4px 20px var(--mint-shadow);
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  border: 1px solid var(--mint-border);
}

.feature-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 28px var(--mint-shadow-hover);
}

.feature-icon {
  margin-bottom: 16px;
  color: var(--mint-primary);
}

.feature-card h3 {
  color: var(--mint-text);
  margin-bottom: 10px;
}

.feature-card p {
  color: var(--mint-text-muted);
}

.cta-section {
  text-align: center;
  padding: 44px;
  background: linear-gradient(145deg, var(--mint-pale) 0%, var(--mint-bg) 100%);
  border-radius: 18px;
  margin-bottom: 40px;
  border: 1px solid var(--mint-border);
}

.cta-section h2 {
  font-size: 1.8rem;
  margin-bottom: 10px;
  color: var(--mint-text);
}

.cta-section p {
  color: var(--mint-text-muted);
  margin-bottom: 24px;
}

.cta-button {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  background: linear-gradient(135deg, var(--mint-primary) 0%, var(--mint-dark) 100%);
  color: white;
  padding: 14px 28px;
  border-radius: 12px;
  font-weight: 600;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.cta-button:hover {
  transform: scale(1.03);
  box-shadow: 0 6px 20px var(--mint-shadow-hover);
}

.demo-section {
  margin-top: 40px;
}

.demo-section h2 {
  text-align: center;
  font-size: 1.8rem;
  margin-bottom: 10px;
  color: var(--mint-text);
}

.section-subtitle {
  text-align: center;
  color: var(--mint-text-muted);
  margin-bottom: 30px;
}

.demo-students {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}
</style>
