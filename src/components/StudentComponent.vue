<template>
  <div class="student-card" :class="{ 'expanded': isExpanded }">
    <div class="student-header" @click="toggleExpand">
      <div class="student-info">
        <h3 class="student-name">{{ studentName }}</h3>
        <p class="student-course">{{ course }}</p>
        <p class="student-year">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="14" height="14">
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm.5-13H11v6l5.25 3.15.75-1.23-4.5-2.67z"/>
          </svg>
          Year: {{ year }}
        </p>
      </div>
      <button 
        class="toggle-btn" 
        @click.stop="toggleExpand"
      >
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
          <path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"/>
        </svg>
      </button>
    </div>
    
    <div v-if="isExpanded" class="student-details">
      <div class="detail-row">
        <span class="detail-label">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="16" height="16">
            <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
          </svg>
          Student ID:
        </span>
        <span class="detail-value">{{ studentId }}</span>
      </div>
      <div class="detail-row">
        <span class="detail-label">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="16" height="16">
            <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
          </svg>
          Email:
        </span>
        <span class="detail-value">{{ email }}</span>
      </div>
      <div class="detail-row">
        <span class="detail-label">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="16" height="16">
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
          </svg>
          Status:
        </span>
        <span class="status-badge" :class="status.toLowerCase()">{{ status }}</span>
      </div>
      
      <div class="actions">
        <button 
          class="action-btn view-btn" 
          @click="$emit('view-details', student)"
        >
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="16" height="16">
            <path d="M12 4.5C7 4.5 2.73 7.61 1 12c1.73 4.39 6 7.5 11 7.5s9.27-3.11 11-7.5c-1.73-4.39-6-7.5-11-7.5zM12 17c-2.76 0-5-2.24-5-5s2.24-5 5-5 5 2.24 5 5-2.24 5-5 5zm0-8c-1.66 0-3 1.34-3 3s1.34 3 3 3 3-1.34 3-3-1.34-3-3-3z"/>
          </svg>
          View Full Details
        </button>
        <button 
          class="action-btn edit-btn" 
          @click="$emit('edit-student', student)"
        >
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="16" height="16">
            <path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04c.39-.39.39-1.02 0-1.41l-2.34-2.34c-.39-.39-1.02-.39-1.41 0l-1.83 1.83 3.75 3.75 1.83-1.83z"/>
          </svg>
          Edit
        </button>
      </div>
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
.student-card {
  background: linear-gradient(135deg, #EEEEEE 0%, #d4d4d4 100%);
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(33, 60, 81, 0.15);
  overflow: hidden;
  transition: all 0.3s ease;
  border: 1px solid #6594B1;
}

.student-card:hover {
  box-shadow: 0 4px 15px rgba(33, 60, 81, 0.25);
  transform: translateY(-2px);
}

.student-card.expanded {
  box-shadow: 0 4px 20px rgba(33, 60, 81, 0.3);
}

.student-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
  cursor: pointer;
}

.student-info {
  flex: 1;
}

.student-name {
  font-size: 1.2rem;
  margin-bottom: 5px;
  color: #213C51;
}

.student-course {
  color: #6594B1;
  font-weight: 600;
  margin-bottom: 5px;
}

.student-year {
  color: #213C51;
  font-size: 0.9rem;
  display: flex;
  align-items: center;
  gap: 5px;
}

.toggle-btn {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: linear-gradient(135deg, #6594B1 0%, #213C51 100%);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.3s ease;
}

.student-card.expanded .toggle-btn {
  transform: rotate(180deg);
}

.student-details {
  padding: 20px;
  border-top: 2px solid #6594B1;
  background: linear-gradient(135deg, #f5f5f5 0%, #EEEEEE 100%);
}

.detail-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
  border-bottom: 1px solid #d4d4d4;
}

.detail-row:last-of-type {
  border-bottom: none;
}

.detail-label {
  display: flex;
  align-items: center;
  gap: 8px;
  color: #6594B1;
  font-weight: 500;
}

.detail-value {
  color: #213C51;
}

.status-badge {
  padding: 4px 12px;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 500;
}

.status-badge.active {
  background: #EEEEEE;
  color: #213C51;
  border: 1px solid #6594B1;
}

.status-badge.inactive {
  background: #DDAED3;
  color: #213C51;
  border: 1px solid #c99dbf;
}

.status-badge.pending {
  background: #EEEEEE;
  color: #6594B1;
  border: 1px solid #6594B1;
}

.actions {
  display: flex;
  gap: 10px;
  margin-top: 15px;
}

.action-btn {
  flex: 1;
  padding: 10px;
  border-radius: 5px;
  font-weight: 500;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}

.view-btn {
  background: linear-gradient(135deg, #6594B1 0%, #213C51 100%);
  color: white;
}

.edit-btn {
  background: linear-gradient(135deg, #87b5c9 0%, #6594B1 100%);
  color: white;
}

.action-btn:hover {
  opacity: 0.9;
  transform: translateY(-1px);
}
</style>
