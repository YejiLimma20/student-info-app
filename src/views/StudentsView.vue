<template>
  <div class="students-page">
    <!-- HEADER -->
    <header class="page-header">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="44" height="44">
        <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
      </svg>
      <h1>Student Directory</h1>
      <p>Manage and view enrolled students</p>
    </header>

    <!-- CONTROLS -->
    <div class="controls">
      <input
        v-model="searchQuery"
        type="text"
        placeholder="Search by name, ID, course, or email..."
        class="search-input"
      />

      <select v-model="selectedYear" class="filter-select">
        <option value="">All Years</option>
        <option value="1">Year 1</option>
        <option value="2">Year 2</option>
        <option value="3">Year 3</option>
        <option value="4">Year 4</option>
      </select>
    </div>

    <!-- STUDENT GRID -->
    <div class="students-grid">
      <div
        v-for="student in filteredStudents"
        :key="student.id"
        class="student-card"
      >
        <div class="avatar">
          {{ student.fullName.charAt(0) }}
        </div>

        <h3>{{ student.fullName }}</h3>

        <div class="student-info">
          <p><strong>ID:</strong> {{ student.id }}</p>
          <p><strong>Course:</strong> {{ student.course }}</p>
          <p><strong>Email:</strong> {{ student.email }}</p>
        </div>

        <div class="meta">
          <span>Year {{ student.year }}</span>
          <span class="status">{{ student.status }}</span>
        </div>

        <button @click="viewStudent(student)">
          View Details
        </button>
      </div>
    </div>

    <!-- FOOTER -->
    <div class="stats-footer">
      Showing {{ filteredStudents.length }} of {{ students.length }} students
    </div>

    <!-- MODAL -->
    <div v-if="showModal" class="modal-overlay" @click.self="closeModal">
      <div class="modal">
        <h2>{{ selectedStudent.fullName }}</h2>
        <p><strong>ID:</strong> {{ selectedStudent.id }}</p>
        <p><strong>Email:</strong> {{ selectedStudent.email }}</p>
        <p><strong>Course:</strong> {{ selectedStudent.course }}</p>
        <p><strong>Year:</strong> {{ selectedStudent.year }}</p>
        <p><strong>Status:</strong> {{ selectedStudent.status }}</p>

        <button class="close-btn" @click="closeModal">Close</button>
      </div>
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
<<<<<<< HEAD
import { ref, computed, onMounted } from 'vue'
import StudentComponent from '../components/StudentComponent.vue'
import EditStudentModal from '../components/EditStudentModal.vue'
=======
import { ref, computed } from 'vue'
>>>>>>> fc77fd55412f11c84ae2adc62ce4f65a5ccd1541

const searchQuery = ref('')
const selectedYear = ref('')

<<<<<<< HEAD
// Modal state
const showEditModal = ref(false)
const selectedStudent = ref(null)

// Computed property for filtering students
const filteredStudents = computed(() => {
  let result = students.value
=======
// STUDENT DATA
const students = ref([
  { id: 'S001', fullName: 'Bernardo Reyes', email: 'bernardo.reyes@gmail.com', course: 'Computer Science', year: 1, status: 'Active' },
  { id: 'S002', fullName: 'Mitchuie Santos', email: 'mitchuie.santos@gmail.com', course: 'Information Technology', year: 2, status: 'Active' },
  { id: 'S003', fullName: 'Zoe Garcia', email: 'zoe.garcia@gmail.com', course: 'Software Engineering', year: 3, status: 'Active' },
  { id: 'S004', fullName: 'Mucho Dela Cruz', email: 'mucho.delacruz@gmail.com', course: 'Data Science', year: 4, status: 'Active' },
  { id: 'S005', fullName: 'Cleo Navarro', email: 'cleo.navarro@gmail.com', course: 'Cyber Security', year: 2, status: 'Active' },
  { id: 'S006', fullName: 'Kitkat Mendoza', email: 'kitkat.mendoza@gmail.com', course: 'Web Development', year: 1, status: 'Active' },
  { id: 'S007', fullName: 'CJ Lopez', email: 'cj.lopez@gmail.com', course: 'Mobile Computing', year: 3, status: 'Active' },
  { id: 'S008', fullName: 'Kiesha Fernandez', email: 'kiesha.fernandez@gmail.com', course: 'Information Technology', year: 4, status: 'Active' },
  { id: 'S009', fullName: 'Mikko Ramos', email: 'mikko.ramos@gmail.com', course: 'Computer Science', year: 2, status: 'Active' },
  { id: 'S010', fullName: 'Athena Villanueva', email: 'athena.villanueva@gmail.com', course: 'Data Science', year: 1, status: 'Active' }
])
>>>>>>> fc77fd55412f11c84ae2adc62ce4f65a5ccd1541

// FILTERED STUDENTS
const filteredStudents = computed(() => {
  return students.value.filter(student => {
    const query = searchQuery.value.toLowerCase()
    const matchesSearch =
      student.fullName.toLowerCase().includes(query) ||
      student.id.toLowerCase().includes(query) ||
      student.course.toLowerCase().includes(query) ||
      student.email.toLowerCase().includes(query)

    const matchesYear =
      !selectedYear.value || student.year.toString() === selectedYear.value

    return matchesSearch && matchesYear
  })
})

// MODAL
const selectedStudent = ref(null)
const showModal = ref(false)

const viewStudent = (student) => {
  selectedStudent.value = student
  showModal.value = true
}

const closeModal = () => {
  showModal.value = false
}
</script>

<style scoped>
.students-page {
  max-width: 1200px;
  margin: auto;
  padding: 20px;
  background: #ffffff;
}

/* HEADER */
.page-header {
  text-align: center;
<<<<<<< HEAD
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
=======
  padding: 40px;
  background: linear-gradient(135deg, #6B8E23, #8FBC8F, #CDE6C3);
  border-radius: 15px;
  color: #F5F1E8;
  margin-bottom: 30px;
>>>>>>> fc77fd55412f11c84ae2adc62ce4f65a5ccd1541
}

/* CONTROLS */
.controls {
  display: flex;
  gap: 15px;
  margin-bottom: 30px;
  flex-wrap: wrap;
}

.search-input,
.filter-select {
  padding: 12px 18px;
  border-radius: 25px;
  border: 2px solid #CDE6C3;
  font-size: 1rem;
  flex: 1;
}

/* GRID */
.students-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 25px;
}

/* CARD */
.student-card {
  background: #ffffff;
  border-radius: 18px;
  padding: 25px;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border: 1px solid #8FBC8F;
  box-shadow: 0 4px 12px rgba(0,0,0,0.08);
}

.avatar {
  width: 60px;
  height: 60px;
  margin: 0 auto 15px;
  border-radius: 50%;
  background: #6B8E23;
  color: #F5F1E8;
  font-size: 1.6rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.student-card h3 {
  color: #4F6F52;
  margin-bottom: 15px;
  text-align: center;
}

.student-info p {
  color: #5F7F63;
  margin-bottom: 8px;
  text-align: left;
}

/* META */
.meta {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
  margin-bottom: 15px;
  color: #5F7F63;
  font-weight: 500;
}

/* BUTTON */
button {
  background: #6B8E23;
  color: #F5F1E8;
  padding: 10px 20px;
  border-radius: 25px;
  font-weight: 600;
  width: 100%;
  margin-top: auto;
}

button:hover {
  opacity: 0.9;
}

/* FOOTER */
.stats-footer {
  margin-top: 30px;
  text-align: center;
  padding: 15px;
  background: #ECE5D8;
  border-radius: 10px;
  color: #4F6F52;
}

/* MODAL */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(79, 111, 82, 0.45);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.modal {
  background: #ffffff;
  padding: 30px;
  border-radius: 20px;
  width: 90%;
  max-width: 400px;
  text-align: center;
  box-shadow: 0 8px 25px rgba(0,0,0,0.15);
}

.modal h2 {
  margin-bottom: 20px;
  color: #4F6F52;
}

.modal p {
  margin-bottom: 10px;
  color: #5F7F63;
}

.close-btn {
  margin-top: 20px;
  background: #6B8E23;
  color: #F5F1E8;
  border-radius: 25px;
  padding: 10px 20px;
  font-weight: 600;
  width: 100%;
}

.close-btn:hover {
  opacity: 0.9;
}
</style>
