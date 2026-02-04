<template>
  <div class="contact-page">
    <!-- HEADER -->
    <header class="page-header">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="48" height="48">
        <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
      </svg>
      <h1>Contact Us</h1>
      <p>We’re here to help — reach out anytime</p>
    </header>

    <!-- MAIN CONTENT -->
    <div class="contact-container">
      <!-- CONTACT INFO -->
      <section class="contact-info">
        <div class="info-card">
          <div class="info-icon">📧</div>
          <div class="info-content">
            <h3>Email</h3>
            <p>support@sisplatform.edu</p>
          </div>
        </div>

        <div class="info-card">
          <div class="info-icon">📞</div>
          <div class="info-content">
            <h3>Phone</h3>
            <p>+1 (800) 456-7890</p>
          </div>
        </div>

        <div class="info-card">
          <div class="info-icon">📍</div>
          <div class="info-content">
            <h3>Address</h3>
            <p>
              Innovation Street, Campus Hub<br />
              Green Valley, GV 40210
            </p>
          </div>
        </div>

        <div class="info-card">
          <div class="info-icon">⏰</div>
          <div class="info-content">
            <h3>Business Hours</h3>
            <p>
              Monday – Friday: 8:00 AM – 5:00 PM<br />
              Saturday: 9:00 AM – 1:00 PM
            </p>
          </div>
        </div>
      </section>

      <!-- CONTACT FORM -->
      <section class="contact-form-section">
        <h2>Send Us a Message</h2>

        <form class="contact-form" @submit.prevent="handleSubmit">
          <div class="form-group">
            <label>Your Name</label>
            <input v-model="formData.name" type="text" placeholder="Your full name" required />
          </div>

          <div class="form-group">
            <label>Email Address</label>
            <input v-model="formData.email" type="email" placeholder="you@example.com" required />
          </div>

          <div class="form-group">
            <label>Subject</label>
            <input v-model="formData.subject" type="text" placeholder="What is this about?" required />
          </div>

          <div class="form-group">
            <label>Message</label>
            <textarea
              v-model="formData.message"
              rows="5"
              placeholder="Tell us how we can help you..."
              required
            ></textarea>
          </div>

          <button type="submit" class="submit-btn">Send Message</button>
        </form>
      </section>
    </div>

    <!-- FAQ -->
    <section class="faq-section">
      <h2>Frequently Asked Questions</h2>
      <div class="faq-list">
        <div class="faq-item" v-for="(faq, index) in faqs" :key="index">
          <div class="faq-question" @click="toggleFaq(index)">
            {{ faq.question }}
            <span :class="{ rotated: faqOpen === index }">⌄</span>
          </div>
          <div class="faq-answer" v-show="faqOpen === index">
            {{ faq.answer }}
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
  { question: 'How can I contact support?', answer: 'You can reach us through email, phone, or by submitting this contact form.' },
  { question: 'How fast do you respond?', answer: 'We typically respond within 24 business hours.' },
  { question: 'Can I request a system demo?', answer: 'Yes, simply send us a message and our team will contact you.' },
  { question: 'Is technical assistance available?', answer: 'Yes, our technical support team is available during business hours.' }
]

const toggleFaq = (index) => {
  faqOpen.value = faqOpen.value === index ? null : index
}

const handleSubmit = () => {
  alert(`Thank you, ${formData.value.name}! Your message has been sent.`)
  formData.value = { name: '', email: '', subject: '', message: '' }
}
</script>

<style scoped>
.contact-page {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.page-header {
  text-align: center;
  padding: 40px;
  background: linear-gradient(135deg, #6B8E23, #8FBC8F, #CDE6C3);
  border-radius: 15px;
  margin-bottom: 40px;
  color: #F5F1E8;
}

.contact-container {
  display: flex;
  gap: 40px;
  flex-wrap: wrap;
  margin-bottom: 50px;
}

/* CONTACT INFO */
.contact-info {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.info-card {
  display: flex;
  align-items: center;
  gap: 15px;
  padding: 20px;
  border-radius: 12px;
  background: #ffffff; /* White background */
  border: 1px solid #8FBC8F;
  box-shadow: 0 4px 10px rgba(0,0,0,0.08);
}

.info-icon {
  font-size: 28px;
  color: #6B8E23;
}

.info-content h3 {
  margin: 0 0 5px 0;
  color: #4F6F52;
}

.info-content p {
  margin: 0;
  color: #5F7F63;
}

/* CONTACT FORM */
.contact-form-section {
  flex: 2;
  background: #ffffff; /* White background */
  padding: 25px;
  border-radius: 12px;
  border: 1px solid #8FBC8F;
  box-shadow: 0 4px 10px rgba(0,0,0,0.08);
}

.contact-form-section h2 {
  color: #4F6F52;
  margin-bottom: 20px;
}

.form-group {
  margin-bottom: 15px;
}

input,
textarea {
  width: 100%;
  padding: 12px;
  border-radius: 8px;
  border: 2px solid #CDE6C3;
  font-size: 1rem;
}

.submit-btn {
  background: #6B8E23;
  color: #F5F1E8;
  padding: 14px;
  width: 100%;
  border-radius: 8px;
  font-weight: bold;
  cursor: pointer;
}

/* FAQ */
.faq-section h2 {
  color: #4F6F52;
  margin-bottom: 20px;
  text-align: center;
}

.faq-list {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.faq-item {
  background: #ffffff; /* White background */
  padding: 15px;
  border-radius: 10px;
  border: 1px solid #8FBC8F;
  box-shadow: 0 3px 8px rgba(0,0,0,0.08);
}

.faq-question {
  display: flex;
  justify-content: space-between;
  cursor: pointer;
  font-weight: 600;
  color: #4F6F52;
}

.faq-answer {
  margin-top: 10px;
  color: #5F7F63;
}

.rotated {
  transform: rotate(180deg);
}

/* RESPONSIVE */
@media (max-width: 900px) {
  .contact-container {
    flex-direction: column;
  }
}
</style>
