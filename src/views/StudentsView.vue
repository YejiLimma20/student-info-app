<template>
  <div class="students-page">
    <header class="page-header">
      <div class="header-icon">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="40" height="40">
          <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
        </svg>
      </div>
      <h1>Student Directory</h1>
      <p>Browse and manage all registered student</p>
    </header>

    <div class="controls">
      <div class="search-box">
        <input 
          v-model="searchQuery" 
          type="text" 
          placeholder="Search students..."
          class="search-input"
        />
      </div>
      <div class="filter-controls">
        <select v-model="selectedYear" class="filter-select">
          <option value="">All Years</option>
          <option value="1">Year 1</option>
          <option value="2">Year 2</option>
          <option value="3">Year 3</option>
          <option value="4">Year 4</option>
        </select>
        <button class="refresh-btn" @click="fetchStudents" :disabled="isLoading">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="18" height="18">
            <path d="M17.65 6.35A7.958 7.958 0 0012 4c-4.42 0-7.99 3.58-7.99 8s3.57 8 7.99 8c3.73 0 6.84-2.55 7.73-6h-2.08A5.99 5.99 0 0112 18c-3.31 0-6-2.69-6-6s2.69-6 6-6c1.66 0 3.14.69 4.22 1.78L13 11h7V4l-2.35 2.35z"/>
          </svg>
          Refresh
        </button>
      </div>
    </div>

    <!-- Loading State -->
    <div v-if="isLoading" class="loading-state">
      <div class="loading-spinner"></div>
      <p>Loading students...</p>
    </div>

    <!-- Error State -->
    <div v-else-if="error" class="error-state">
      <div class="error-icon">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="48" height="48">
          <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 15h-2v-2h2v2zm0-4h-2V7h2v6z"/>
        </svg>
      </div>
      <h3>Oops! Something went wrong</h3>
      <p>{{ error }}</p>
      <button class="retry-btn" @click="fetchStudents">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="16" height="16">
          <path d="M17.65 6.35A7.958 7.958 0 0012 4c-4.42 0-7.99 3.58-7.99 8s3.57 8 7.99 8c3.73 0 6.84-2.55 7.73-6h-2.08A5.99 5.99 0 0112 18c-3.31 0-6-2.69-6-6s2.69-6 6-6c1.66 0 3.14.69 4.22 1.78L13 11h7V4l-2.35 2.35z"/>
        </svg>
        Try Again
      </button>
    </div>

    <!-- Empty State -->
    <div v-else-if="filteredStudents.length === 0" class="empty-state">
      <div class="empty-icon">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="48" height="48">
          <path d="M15.5 14h-.79l-.28-.27A6.471 6.471 0 0016 9.5 6.5 6.5 0 109.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/>
        </svg>
      </div>
      <h3>No students found</h3>
      <p>Try adjusting your search or filter criteria</p>
    </div>

    <!-- Student List -->
    <div v-else class="students-grid">
      <StudentComponent
        v-for="student in filteredStudents"
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

    <!-- Stats Footer -->
    <div v-if="!isLoading && !error && students.length > 0" class="stats-footer">
      <span>Showing {{ filteredStudents.length }} of {{ students.length }} students</span>
    </div>

    <!-- Edit Student Modal -->
    <EditStudentModal
      :is-visible="showEditModal"
      :student="selectedStudent"
      @close="closeEditModal"
      @save="handleSaveStudent"
    />
  </div>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'
import StudentComponent from '../components/StudentComponent.vue'
import EditStudentModal from '../components/EditStudentModal.vue'

// State management
const students = ref([])
const isLoading = ref(false)
const error = ref(null)
const searchQuery = ref('')
const selectedYear = ref('')

// Modal state
const showEditModal = ref(false)
const selectedStudent = ref(null)

// Computed property for filtering students
const filteredStudents = computed(() => {
  let result = students.value

  // Filter by search query
  if (searchQuery.value) {
    const query = searchQuery.value.toLowerCase()
    result = result.filter(student => 
      student.name.toLowerCase().includes(query) ||
      student.course.toLowerCase().includes(query) ||
      student.email.toLowerCase().includes(query)
    )
  }

  // Filter by year
  if (selectedYear.value) {
    result = result.filter(student => 
      student.year.toString() === selectedYear.value
    )
  }

  return result
})

// API Integration using Fetch
const fetchStudents = async () => {
  isLoading.value = true
  error.value = null

  try {
    // Using JSONPlaceholder API as public API example
    const response = await fetch('https://jsonplaceholder.typicode.com/users')

    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`)
    }

    const data = await response.json()

    // Transform API data to student format
    students.value = data.map(user => ({
      id: user.id.toString().padStart(4, '0'),
      name: user.name,
      course: getRandomCourse(),
      year: Math.floor(Math.random() * 4) + 1,
      email: user.email,
      status: getRandomStatus(),
      phone: user.phone,
      website: user.website,
      company: user.company.name
    }))

  } catch (err) {
    error.value = err.message || 'Failed to fetch students. Please try again.'
    console.error('Error fetching students:', err)
  } finally {
    isLoading.value = false
  }
}

// Helper functions
const getRandomCourse = () => {
  const courses = [
    'Computer Science',
    'Information Technology',
    'Software Engineering',
    'Data Science',
    'Cyber Security',
    'Web Development',
    'Mobile Computing'
  ]
  return courses[Math.floor(Math.random() * courses.length)]
}

const getRandomStatus = () => {
  const statuses = ['Active', 'Active', 'Active', 'Pending', 'Inactive']
  return statuses[Math.floor(Math.random() * statuses.length)]
}

// Event handlers
const handleViewDetails = (student) => {
  console.log('View details for:', student)
  alert(`Viewing details for:\n\nName: ${student.name}\nCourse: ${student.course}\nYear: ${student.year}\nEmail: ${student.email}`)
}

const handleEditStudent = (student) => {
  console.log('Edit student:', student)
  alert(`Opening editor for ${student.name}`)
}

// Fetch data on component mount
onMounted(() => {
  fetchStudents()
})
</script>

<style scoped>
.students-page {
  max-width: 1200px;
  margin: 0 auto;
}

.page-header {
  text-align: center;
  margin-bottom: 40px;
  padding: 3rem 2rem;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  border-radius: 24px;
  color: #2d3748;
  border: 1px solid rgba(255, 255, 255, 0.2);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
  position: relative;
  overflow: hidden;
  animation: slideInDown 0.8s cubic-bezier(0.4, 0, 0.2, 1);
}

.page-header::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.05) 0%, rgba(118, 75, 162, 0.05) 100%);
  z-index: -1;
  animation: shimmer 3s ease-in-out infinite;
}

@keyframes slideInDown {
  from {
    opacity: 0;
    transform: translateY(-30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes shimmer {
  0%, 100% {
    opacity: 0.05;
  }
  50% {
    opacity: 0.1;
  }
}

.header-icon {
  display: flex;
  justify-content: center;
  margin-bottom: 1rem;
}

.header-icon svg {
  color: #667eea;
  background: rgba(102, 126, 234, 0.1);
  border-radius: 12px;
  padding: 0.5rem;
}

.page-header h1 {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: #2d3748;
}

.page-header p {
  font-size: 1.125rem;
  color: #718096;
}

.controls {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 30px;
  gap: 20px;
  flex-wrap: wrap;
}

.search-box {
  flex: 1;
  min-width: 250px;
}

.search-input {
  width: 100%;
  padding: 12px 20px;
  border: 2px solid #6594B1;
  border-radius: 25px;
  font-size: 1rem;
  transition: border-color 0.3s ease;
  background: white;
}

.search-input:focus {
  outline: none;
  border-color: #213C51;
  box-shadow: 0 0 0 3px rgba(101, 148, 177, 0.2);
}

.filter-controls {
  display: flex;
  gap: 10px;
}

.filter-select {
  padding: 12px 20px;
  border: 2px solid #6594B1;
  border-radius: 25px;
  font-size: 1rem;
  background: white;
  cursor: pointer;
}

.filter-select:focus {
  outline: none;
  border-color: #213C51;
}

.refresh-btn {
  padding: 12px 20px;
  background: linear-gradient(135deg, #6594B1 0%, #213C51 100%);
  color: white;
  border-radius: 25px;
  display: flex;
  align-items: center;
  gap: 8px;
}

.refresh-btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.loading-state {
  text-align: center;
  padding: 60px 20px;
  background: #EEEEEE;
  border-radius: 10px;
}

.loading-spinner {
  width: 50px;
  height: 50px;
  border: 4px solid #d4d4d4;
  border-top-color: #6594B1;
  border-radius: 50%;
  margin: 0 auto 20px;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

.error-state {
  text-align: center;
  padding: 60px 20px;
  background: #ffebee;
  border-radius: 10px;
  border: 2px solid #ef5350;
}

.error-icon {
  margin-bottom: 15px;
  color: #c62828;
}

.error-state h3 {
  color: #c62828;
  margin-bottom: 10px;
}

.error-state p {
  color: #666;
  margin-bottom: 20px;
}

.retry-btn {
  background: linear-gradient(135deg, #4caf50 0%, #2e7d32 100%);
  color: white;
  padding: 12px 30px;
  display: inline-flex;
  align-items: center;
  gap: 8px;
}

.empty-state {
  text-align: center;
  padding: 60px 20px;
  background: #e8f5e9;
  border-radius: 10px;
}

.empty-icon {
  margin-bottom: 15px;
  color: #4caf50;
}

.empty-state h3 {
  color: #2e7d32;
  margin-bottom: 10px;
}

.empty-state p {
  color: #666;
}

.students-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

.stats-footer {
  text-align: center;
  padding: 20px;
  color: #2e7d32;
  background: #e8f5e9;
  border-radius: 10px;
  margin-top: 30px;
}
</style>
