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
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import StudentComponent from '../components/StudentComponent.vue'

// Static student data (same list as Home featured students)
const STUDENT_LIST = [
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
]

// State management
const students = ref([...STUDENT_LIST])
const isLoading = ref(false)
const error = ref(null)
const searchQuery = ref('')
const selectedYear = ref('')

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

// Refresh just re-loads the static list (no API)
const fetchStudents = () => {
  isLoading.value = true
  error.value = null
  setTimeout(() => {
    students.value = [...STUDENT_LIST]
    isLoading.value = false
  }, 300)
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

// Data is loaded from static list (no API fetch on mount)
</script>

<style scoped>
.students-page {
  max-width: 1200px;
  margin: 0 auto;
}

.page-header {
  text-align: center;
  margin-bottom: 30px;
  padding: 32px;
  background: linear-gradient(145deg, var(--mint-dark) 0%, var(--mint-primary) 60%, var(--mint-mid) 100%);
  border-radius: 18px;
  color: white;
  box-shadow: 0 8px 32px var(--mint-shadow);
}

.header-icon {
  display: flex;
  justify-content: center;
  margin-bottom: 15px;
}

.page-header h1 {
  font-size: 2rem;
  margin-bottom: 10px;
  color: white;
}

.page-header p {
  color: rgba(255, 255, 255, 0.9);
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
  border: 2px solid var(--mint-border);
  border-radius: 12px;
  font-size: 1rem;
  transition: border-color 0.2s ease, box-shadow 0.2s ease;
  background: white;
}

.search-input:focus {
  outline: none;
  border-color: var(--mint-primary);
  box-shadow: 0 0 0 3px var(--mint-shadow);
}

.filter-controls {
  display: flex;
  gap: 10px;
}

.filter-select {
  padding: 12px 20px;
  border: 2px solid var(--mint-border);
  border-radius: 12px;
  font-size: 1rem;
  background: white;
  cursor: pointer;
}

.filter-select:focus {
  outline: none;
  border-color: var(--mint-primary);
}

.refresh-btn {
  padding: 12px 20px;
  background: linear-gradient(135deg, var(--mint-primary) 0%, var(--mint-dark) 100%);
  color: white;
  border-radius: 12px;
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
  background: var(--mint-white);
  border-radius: 14px;
  border: 1px solid var(--mint-border);
}

.loading-spinner {
  width: 50px;
  height: 50px;
  border: 4px solid var(--mint-pale);
  border-top-color: var(--mint-primary);
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
  background: linear-gradient(135deg, var(--mint-primary) 0%, var(--mint-dark) 100%);
  color: white;
  padding: 12px 30px;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  border-radius: 12px;
}

.empty-state {
  text-align: center;
  padding: 60px 20px;
  background: var(--mint-bg);
  border-radius: 14px;
  border: 1px solid var(--mint-border);
}

.empty-icon {
  margin-bottom: 15px;
  color: var(--mint-primary);
}

.empty-state h3 {
  color: var(--mint-text);
  margin-bottom: 10px;
}

.empty-state p {
  color: var(--mint-text-muted);
}

.students-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

.stats-footer {
  text-align: center;
  padding: 20px;
  color: var(--mint-text);
  background: var(--mint-pale);
  border-radius: 14px;
  margin-top: 30px;
  border: 1px solid var(--mint-border);
}
</style>
