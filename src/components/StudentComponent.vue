<template>
  <div class="student-tile" :class="{ 'expanded': isExpanded }" @click="toggleExpand">
    <div class="tile-header">
      <div class="avatar">
        {{ studentName.charAt(0).toUpperCase() }}
      </div>
      <div class="tile-content">
        <h3 class="student-name">{{ studentName }}</h3>
        <div class="meta-info">
          <span class="course-badge">{{ course }}</span>
          <span class="year-info">Year {{ year }}</span>
        </div>
      </div>
    </div>

    <div v-if="isExpanded" class="tile-details">
      <div class="detail-grid">
        <div class="detail-item">
          <div class="detail-icon">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="16" height="16">
              <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
            </svg>
          </div>
          <div class="detail-content">
            <div class="detail-label">Student ID</div>
            <div class="detail-value">{{ studentId }}</div>
          </div>
        </div>
        <div class="detail-item">
          <div class="detail-icon">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="16" height="16">
              <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
            </svg>
          </div>
          <div class="detail-content">
            <div class="detail-label">Email</div>
            <div class="detail-value">{{ email }}</div>
          </div>
        </div>
      </div>

      <div class="tile-actions">
        <button
          class="action-btn secondary"
          @click.stop="$emit('edit-student', student)"
        >
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="16" height="16">
            <path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04c.39-.39.39-1.02 0-1.41l-2.34-2.34c-.39-.39-1.02-.39-1.41 0l-1.83 1.83 3.75 3.75 1.83-1.83z"/>
          </svg>
          Edit
        </button>
        <button
          class="action-btn primary"
          @click.stop="$emit('view-details', student)"
        >
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="16" height="16">
            <path d="M12 4.5C7 4.5 2.73 7.61 1 12c1.73 4.39 6 7.5 11 7.5s9.27-3.11 11-7.5c-1.73-4.39-6-7.5-11-7.5zM12 17c-2.76 0-5-2.24-5-5s2.24-5 5-5 5 2.24 5 5-2.24 5-5 5zm0-8c-1.66 0-3 1.34-3 3s1.34 3 3 3 3-1.34 3-3-1.34-3-3-3z"/>
          </svg>
          View Details
        </button>
      </div>
    </div>

    <div class="expand-indicator" :class="{ 'expanded': isExpanded }">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
        <path d="M7 10l5 5 5-5z"/>
      </svg>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// Props for passing student data
const props = defineProps({
  student: {
    type: Object,
    required: true
  },
  studentName: {
    type: String,
    required: true
  },
  course: {
    type: String,
    required: true
  },
  year: {
    type: [Number, String],
    required: true
  },
  studentId: {
    type: String,
    default: 'N/A'
  },
  email: {
    type: String,
    default: 'N/A'
  },
  status: {
    type: String,
    default: 'Active'
  }
})

// Component state
const isExpanded = ref(false)

// Event handlers
const toggleExpand = () => {
  isExpanded.value = !isExpanded.value
}

// Define emits
defineEmits(['view-details', 'edit-student'])
</script>

<style scoped>
<<<<<<< HEAD
.student-card {
  background: linear-gradient(145deg, var(--mint-white) 0%, var(--mint-bg) 100%);
  border-radius: 14px;
  box-shadow: 0 4px 20px var(--mint-shadow);
  overflow: hidden;
  transition: all 0.25s ease;
  border: 1px solid var(--mint-border);
}

.student-card:hover {
  box-shadow: 0 8px 28px var(--mint-shadow-hover);
  transform: translateY(-2px);
}

.student-card.expanded {
  box-shadow: 0 8px 32px var(--mint-shadow-hover);
}

.student-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
=======
.student-tile {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  border-radius: 16px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  overflow: hidden;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
  cursor: pointer;
  border: 1px solid rgba(255, 255, 255, 0.2);
  position: relative;
  transform: translateZ(0);
}

.student-tile:hover {
  transform: translateY(-6px) scale(1.02);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.15);
}

.student-tile.expanded {
  box-shadow: 0 8px 35px rgba(0, 0, 0, 0.12);
}

.tile-header {
  display: flex;
  align-items: center;
  padding: 1.5rem;
  gap: 1rem;
}

.avatar {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);
}

.tile-content {
  flex: 1;
}

.student-name {
<<<<<<< HEAD
  font-size: 1.2rem;
  margin-bottom: 5px;
  color: var(--mint-text);
}

.student-course {
  color: var(--mint-text-muted);
=======
  font-size: 1.25rem;
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
  font-weight: 600;
  color: #2d3748;
  margin: 0 0 0.5rem 0;
}

<<<<<<< HEAD
.student-year {
  color: var(--mint-text);
  font-size: 0.9rem;
=======
.meta-info {
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

<<<<<<< HEAD
.toggle-btn {
  width: 38px;
  height: 38px;
  border-radius: 12px;
  background: linear-gradient(135deg, var(--mint-primary) 0%, var(--mint-dark) 100%);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.25s ease;
=======
.course-badge {
  background: rgba(102, 126, 234, 0.1);
  color: #667eea;
  padding: 0.25rem 0.75rem;
  border-radius: 20px;
  font-size: 0.875rem;
  font-weight: 500;
}

.year-info {
  color: #718096;
  font-size: 0.875rem;
}

.tile-details {
  padding: 1.5rem;
  border-top: 1px solid rgba(0, 0, 0, 0.05);
  background: rgba(248, 250, 252, 0.5);
}

.detail-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.detail-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
}

.detail-icon {
  color: #667eea;
  background: rgba(102, 126, 234, 0.1);
  border-radius: 8px;
  padding: 0.5rem;
}

<<<<<<< HEAD
.student-details {
  padding: 20px;
  border-top: 2px solid var(--mint-border);
  background: linear-gradient(145deg, var(--mint-bg) 0%, var(--mint-pale) 100%);
}

.detail-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
  border-bottom: 1px solid var(--mint-border);
}

.detail-row:last-of-type {
  border-bottom: none;
}

.detail-label {
  display: flex;
  align-items: center;
  gap: 8px;
  color: var(--mint-text-muted);
  font-weight: 500;
}

.detail-value {
  color: var(--mint-text);
}

.status-badge {
  padding: 4px 12px;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 500;
}

.status-badge.active {
  background: var(--mint-pale);
  color: var(--mint-text);
  border: 1px solid var(--mint-mid);
}

.status-badge.inactive {
  background: #ffebee;
  color: #b71c1c;
  border: 1px solid #ef9a9a;
}

.status-badge.pending {
  background: var(--mint-bg);
  color: var(--mint-text-muted);
  border: 1px solid var(--mint-border);
}

.actions {
=======
.detail-content {
  display: flex;
  flex-direction: column;
}

.detail-label {
  font-size: 0.75rem;
  color: #a0aec0;
  text-transform: uppercase;
  font-weight: 600;
  letter-spacing: 0.05em;
}

.detail-value {
  font-size: 0.875rem;
  color: #2d3748;
  font-weight: 500;
}

.tile-actions {
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
  display: flex;
  gap: 0.75rem;
}

.action-btn {
  flex: 1;
  padding: 0.75rem 1rem;
  border-radius: 8px;
  font-weight: 600;
  font-size: 0.875rem;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  border: none;
  cursor: pointer;
}

<<<<<<< HEAD
.view-btn {
  background: linear-gradient(135deg, var(--mint-primary) 0%, var(--mint-dark) 100%);
=======
.action-btn.primary {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
  color: white;
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);
}

<<<<<<< HEAD
.edit-btn {
  background: linear-gradient(135deg, var(--mint-mid) 0%, var(--mint-primary) 100%);
  color: white;
=======
.action-btn.secondary {
  background: rgba(113, 128, 150, 0.1);
  color: #4a5568;
  border: 1px solid rgba(113, 128, 150, 0.2);
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
}

.action-btn:hover {
  transform: translateY(-2px);
}

.action-btn.primary:hover {
  box-shadow: 0 6px 20px rgba(102, 126, 234, 0.4);
}

.expand-indicator {
  position: absolute;
  bottom: 1rem;
  right: 1rem;
  width: 32px;
  height: 32px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  display: flex;
  align-items: center;
  justify-content: center;
  color: #667eea;
  transition: transform 0.3s ease;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.expand-indicator.expanded {
  transform: rotate(180deg);
}
</style>
