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

<<<<<<< HEAD
=======
<<<<<<< HEAD
>>>>>>> d3e1d1395714ed52494885ed674062b9ff2996b1
    <!-- Edit Student Modal -->
    <EditStudentModal
      :is-visible="showEditModal"
      :student="selectedStudent"
      @close="closeEditModal"
      @save="handleSaveStudent"
    />
<<<<<<< HEAD
=======
=======
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

>>>>>>> fc77fd55412f11c84ae2adc62ce4f65a5ccd1541
>>>>>>> d3e1d1395714ed52494885ed674062b9ff2996b1
  </div>
</template>

<script setup>
import { ref } from 'vue'
<<<<<<< HEAD
import StudentComponent from '../components/StudentComponent.vue'
import EditStudentModal from '../components/EditStudentModal.vue'
<<<<<<< HEAD
=======
=======
>>>>>>> fc77fd55412f11c84ae2adc62ce4f65a5ccd1541
>>>>>>> d3e1d1395714ed52494885ed674062b9ff2996b1

<<<<<<< HEAD
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
=======
const navCards = [
  { icon: '📚', title: 'Manage Students', description: 'Add, edit, or view student records' },
  { icon: '📊', title: 'Reports', description: 'Generate academic reports and analytics' },
  { icon: '🔔', title: 'Notifications', description: 'View announcements and updates' }
]

<<<<<<< HEAD
// Modal state
const showEditModal = ref(false)
const selectedStudent = ref(null)
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4

// Modal state
const showEditModal = ref(false)
const selectedStudent = ref(null)

// Event handlers
const handleViewDetails = (student) => {
  console.log('View details for:', student)
  alert(`Viewing details for ${student.name}`)
}

const handleEditStudent = (student) => {
  selectedStudent.value = student
  showEditModal.value = true
<<<<<<< HEAD
}

const closeEditModal = () => {
  showEditModal.value = false
  selectedStudent.value = null
}

const handleSaveStudent = (updatedStudent) => {
  const index = featuredStudents.value.findIndex(student => student.id === updatedStudent.id)
  if (index !== -1) {
    featuredStudents.value[index] = updatedStudent
    console.log('Student updated:', updatedStudent)
  }
  closeEditModal()
=======
>>>>>>> d3e1d1395714ed52494885ed674062b9ff2996b1
}

const closeEditModal = () => {
  showEditModal.value = false
  selectedStudent.value = null
}

const handleSaveStudent = (updatedStudent) => {
  const index = featuredStudents.value.findIndex(student => student.id === updatedStudent.id)
  if (index !== -1) {
    featuredStudents.value[index] = updatedStudent
    console.log('Student updated:', updatedStudent)
  }
  closeEditModal()
}
=======
const announcements = [
  { id: 1, date: '2026-02-01', text: 'New semester registration starts next week.' },
  { id: 2, date: '2026-01-20', text: 'Maintenance scheduled on 2026-02-10.' },
  { id: 3, date: '2026-01-15', text: 'New courses added for Spring 2026.' }
]
>>>>>>> fc77fd55412f11c84ae2adc62ce4f65a5ccd1541
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
<<<<<<< HEAD
  padding: 56px 24px;
  background: linear-gradient(145deg, var(--mint-dark) 0%, var(--mint-primary) 60%, var(--mint-mid) 100%);
  color: white;
  border-radius: 18px;
  margin-bottom: 40px;
  box-shadow: 0 8px 32px var(--mint-shadow);
=======
  border: 1px solid #8FBC8F;
  box-shadow: 0 8px 20px rgba(0,0,0,0.08);
  transition: transform 0.3s, box-shadow 0.3s;
  cursor: pointer;
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
}

.card:hover {
  transform: translateY(-10px);
  box-shadow: 0 12px 25px rgba(0,0,0,0.15);
}

.card-icon {
  font-size: 2.5rem;
  margin-bottom: 15px;
}

<<<<<<< HEAD
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
=======
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
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
</style>
