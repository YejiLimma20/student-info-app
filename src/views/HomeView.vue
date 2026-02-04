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
  {
    id: '2024001',
    name: 'John Smith',
    course: 'Computer Science',
    year: 3,
    email: 'john.smith@school.edu',
    status: 'Active'
  },
  {
    id: '2024002',
    name: 'Emily Johnson',
    course: 'Information Technology',
    year: 2,
    email: 'emily.j@school.edu',
    status: 'Active'
  },
  {
    id: '2024003',
    name: 'Michael Brown',
    course: 'Software Engineering',
    year: 4,
    email: 'michael.b@school.edu',
    status: 'Active'
  }
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
  padding: 60px 20px;
  background: linear-gradient(135deg, #213C51 0%, #6594B1 50%, #87b5c9 100%);
  color: white;
  border-radius: 15px;
  margin-bottom: 40px;
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
  background: linear-gradient(135deg, #EEEEEE 0%, #d4d4d4 100%);
  border-radius: 10px;
  padding: 30px;
  text-align: center;
  box-shadow: 0 2px 10px rgba(33, 60, 81, 0.15);
  transition: transform 0.3s ease;
  border: 1px solid #6594B1;
}

.feature-card:hover {
  transform: translateY(-5px);
}

.feature-icon {
  margin-bottom: 15px;
  color: #6594B1;
}

.feature-card h3 {
  color: #213C51;
  margin-bottom: 10px;
}

.feature-card p {
  color: #6594B1;
}

.cta-section {
  text-align: center;
  padding: 40px;
  background: linear-gradient(135deg, #f5f5f5 0%, #EEEEEE 100%);
  border-radius: 15px;
  margin-bottom: 40px;
  border: 1px solid #6594B1;
}

.cta-section h2 {
  font-size: 1.8rem;
  margin-bottom: 10px;
  color: #213C51;
}

.cta-section p {
  color: #6594B1;
  margin-bottom: 20px;
}

.cta-button {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  background: linear-gradient(135deg, #6594B1 0%, #213C51 100%);
  color: white;
  padding: 15px 30px;
  border-radius: 25px;
  font-weight: bold;
  transition: transform 0.3s ease;
}

.cta-button:hover {
  transform: scale(1.05);
}

.demo-section {
  margin-top: 40px;
}

.demo-section h2 {
  text-align: center;
  font-size: 1.8rem;
  margin-bottom: 10px;
  color: #213C51;
}

.section-subtitle {
  text-align: center;
  color: #6594B1;
  margin-bottom: 30px;
}

.demo-students {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}
</style>
