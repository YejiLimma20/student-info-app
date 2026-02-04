<template>
  <div class="contact-page">
    <header class="page-header">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="48" height="48">
        <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
      </svg>
      <h1>Contact Us</h1>
      <p>Get in touch with our team</p>
    </header>

    <div class="contact-container">
      <section class="contact-info">
        <div class="info-card">
          <div class="info-icon">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="32" height="32">
              <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
            </svg>
          </div>
          <div class="info-content">
            <h3>Email</h3>
            <p>support@studentinfo.edu</p>
          </div>
        </div>

        <div class="info-card">
          <div class="info-icon">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="32" height="32">
              <path d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z"/>
            </svg>
          </div>
          <div class="info-content">
            <h3>Phone</h3>
            <p>+1 (555) 123-4567</p>
          </div>
        </div>

        <div class="info-card">
          <div class="info-icon">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="32" height="32">
              <path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/>
            </svg>
          </div>
          <div class="info-content">
            <h3>Address</h3>
            <p>123 Education Lane<br>Tech City, TC 12345</p>
          </div>
        </div>

        <div class="info-card">
          <div class="info-icon">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="32" height="32">
              <path d="M11.99 2C6.47 2 2 6.48 2 12s4.47 10 9.99 10C17.52 22 22 17.52 22 12S17.52 2 11.99 2zM12 20c-4.42 0-8-3.58-8-8s3.58-8 8-8 8 3.58 8 8-3.58 8-8 8zm.5-13H11v6l5.25 3.15.75-1.23-4.5-2.67z"/>
            </svg>
          </div>
          <div class="info-content">
            <h3>Business Hours</h3>
            <p>Monday - Friday: 9:00 AM - 6:00 PM<br>Saturday: 10:00 AM - 4:00 PM</p>
          </div>
        </div>
      </section>

      <section class="contact-form-section">
        <h2>Send us a Message</h2>
        <form class="contact-form" @submit.prevent="handleSubmit">
          <div class="form-group">
            <label for="name">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="18" height="18">
                <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
              </svg>
              Your Name
            </label>
            <input 
              id="name"
              v-model="formData.name" 
              type="text" 
              placeholder="Enter your name"
              required
            />
          </div>

          <div class="form-group">
            <label for="email">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="18" height="18">
                <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
              </svg>
              Email Address
            </label>
            <input 
              id="email"
              v-model="formData.email" 
              type="email" 
              placeholder="Enter your email"
              required
            />
          </div>

          <div class="form-group">
            <label for="subject">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="18" height="18">
                <path d="M20 2H4c-1.1 0-1.99.9-1.99 2L2 22l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm-2 12H6v-2h12v2zm0-3H6V9h12v2zm0-3H6V6h12v2z"/>
              </svg>
              Subject
            </label>
            <input 
              id="subject"
              v-model="formData.subject" 
              type="text" 
              placeholder="Enter subject"
              required
            />
          </div>

          <div class="form-group">
            <label for="message">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="18" height="18">
                <path d="M20 2H4c-1.1 0-1.99.9-1.99 2L2 22l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm-2 12H6v-2h12v2zm0-3H6V9h12v2zm0-3H6V6h12v2z"/>
              </svg>
              Message
            </label>
            <textarea 
              id="message"
              v-model="formData.message" 
              placeholder="Write your message here..."
              rows="5"
              required
            ></textarea>
          </div>

          <button type="submit" class="submit-btn">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
              <path d="M2.01 21L23 12 2.01 3 2 10l15 2-15 2z"/>
            </svg>
            Send Message
          </button>
        </form>
      </section>
    </div>

    <section class="faq-section">
      <h2>Frequently Asked Questions</h2>
      <div class="faq-list">
        <div class="faq-item" v-for="(faq, index) in faqs" :key="index">
          <div class="faq-question" @click="toggleFaq(index)">
            <span>{{ faq.question }}</span>
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="24" height="24" :class="{ 'rotated': faqOpen === index }">
              <path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"/>
            </svg>
          </div>
          <div class="faq-answer" v-show="faqOpen === index">
            <p>{{ faq.answer }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const formData = ref({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const faqOpen = ref(null)

const faqs = [
  {
    question: 'How do I add a new student to the system?',
    answer: 'Navigate to the Students page and click the "Add Student" button. Fill in the required information and click "Save" to add the student to the database.'
  },
  {
    question: 'Can I export student data to CSV or PDF?',
    answer: 'Yes, on the Students page, use the export options available in the controls section. You can choose between CSV or PDF format for your exports.'
  },
  {
    question: 'How do I reset my password?',
    answer: 'Click on the "Forgot Password" link on the login page. Enter your email address and we will send you a password reset link.'
  },
  {
    question: 'Is my data secure?',
    answer: 'We implement industry-standard security measures including encryption, regular backups, and secure API connections to protect your data.'
  }
]

const toggleFaq = (index) => {
  faqOpen.value = faqOpen.value === index ? null : index
}

const handleSubmit = () => {
  alert(`Thank you, ${formData.value.name}! Your message has been sent. We will get back to you at ${formData.value.email} soon.`)
  formData.value = {
    name: '',
    email: '',
    subject: '',
    message: ''
  }
}
</script>

<style scoped>
.contact-page {
  max-width: 1200px;
  margin: 0 auto;
}

.page-header {
  text-align: center;
  padding: 40px;
  background: linear-gradient(135deg, #213C51 0%, #6594B1 50%, #87b5c9 100%);
  border-radius: 15px;
  margin-bottom: 40px;
  color: white;
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
  opacity: 0.9;
}

.contact-container {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 40px;
  margin-bottom: 40px;
}

@media (max-width: 768px) {
  .contact-container {
    grid-template-columns: 1fr;
  }
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.info-card {
  background: linear-gradient(135deg, #f1f8e9 0%, #dcedc8 100%);
  border-radius: 12px;
  padding: 20px;
  display: flex;
  align-items: center;
  gap: 15px;
  border: 1px solid #a5d6a7;
  box-shadow: 0 2px 8px rgba(46, 125, 50, 0.1);
}

.info-icon {
  color: #2e7d32;
  flex-shrink: 0;
}

.info-content h3 {
  color: #1b5e20;
  font-size: 0.9rem;
  margin-bottom: 4px;
}

.info-content p {
  color: #388e3c;
  font-size: 0.95rem;
}

.contact-form-section {
  background: linear-gradient(135deg, #f1f8e9 0%, #dcedc8 100%);
  border-radius: 15px;
  padding: 30px;
  border: 1px solid #a5d6a7;
}

.contact-form-section h2 {
  color: #1b5e20;
  margin-bottom: 25px;
  font-size: 1.5rem;
}

.form-group {
  margin-bottom: 20px;
}

.form-group label {
  display: flex;
  align-items: center;
  gap: 8px;
  color: #2e7d32;
  font-weight: 500;
  margin-bottom: 8px;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 12px 16px;
  border: 2px solid #a5d6a7;
  border-radius: 8px;
  font-size: 1rem;
  transition: border-color 0.3s ease;
  background: white;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #4caf50;
  box-shadow: 0 0 0 3px rgba(76, 175, 80, 0.2);
}

.form-group textarea {
  resize: vertical;
  min-height: 120px;
}

.submit-btn {
  background: linear-gradient(135deg, #4caf50 0%, #2e7d32 100%);
  color: white;
  padding: 14px 28px;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  display: inline-flex;
  align-items: center;
  gap: 10px;
  transition: transform 0.3s ease;
  width: 100%;
  justify-content: center;
}

.submit-btn:hover {
  transform: translateY(-2px);
}

.faq-section {
  background: linear-gradient(135deg, #e8f5e9 0%, #c8e6c9 100%);
  border-radius: 15px;
  padding: 40px;
  border: 1px solid #a5d6a7;
}

.faq-section h2 {
  color: #1b5e20;
  margin-bottom: 25px;
  font-size: 1.5rem;
  text-align: center;
}

.faq-list {
  max-width: 800px;
  margin: 0 auto;
}

.faq-item {
  background: white;
  border-radius: 8px;
  margin-bottom: 10px;
  overflow: hidden;
  border: 1px solid #a5d6a7;
}

.faq-question {
  padding: 16px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
  color: #1b5e20;
  font-weight: 500;
  transition: background-color 0.3s ease;
}

.faq-question:hover {
  background: #f1f8e9;
}

.faq-question svg {
  color: #4caf50;
  transition: transform 0.3s ease;
}

.faq-question svg.rotated {
  transform: rotate(180deg);
}

.faq-answer {
  padding: 0 20px 16px;
  color: #6594B1;
  line-height: 1.6;
}
</style>
