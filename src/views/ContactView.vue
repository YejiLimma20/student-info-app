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
<<<<<<< HEAD
  padding: 44px;
  background: linear-gradient(145deg, var(--mint-dark) 0%, var(--mint-primary) 60%, var(--mint-mid) 100%);
  border-radius: 18px;
  margin-bottom: 40px;
  color: white;
  box-shadow: 0 8px 32px var(--mint-shadow);
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
=======
  padding: 40px;
  background: linear-gradient(135deg, #6B8E23, #8FBC8F, #CDE6C3);
  border-radius: 15px;
  margin-bottom: 40px;
  color: #F5F1E8;
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
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
<<<<<<< HEAD
  background: linear-gradient(145deg, var(--mint-white) 0%, var(--mint-bg) 100%);
  border-radius: 14px;
  padding: 22px;
  display: flex;
  align-items: center;
  gap: 16px;
  border: 1px solid var(--mint-border);
  box-shadow: 0 4px 16px var(--mint-shadow);
}

.info-icon {
  color: var(--mint-primary);
  flex-shrink: 0;
}

.info-content h3 {
  color: var(--mint-text);
  font-size: 0.9rem;
  margin-bottom: 4px;
}

.info-content p {
  color: var(--mint-text-muted);
  font-size: 0.95rem;
=======
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
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
}

/* CONTACT FORM */
.contact-form-section {
<<<<<<< HEAD
  background: linear-gradient(145deg, var(--mint-pale) 0%, var(--mint-bg) 100%);
  border-radius: 18px;
  padding: 32px;
  border: 1px solid var(--mint-border);
}

.contact-form-section h2 {
  color: var(--mint-text);
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
  color: var(--mint-text);
  font-weight: 500;
  margin-bottom: 8px;
=======
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
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
}

input,
textarea {
  width: 100%;
<<<<<<< HEAD
  padding: 12px 16px;
  border: 2px solid var(--mint-border);
  border-radius: 10px;
  font-size: 1rem;
  transition: border-color 0.2s ease, box-shadow 0.2s ease;
  background: white;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--mint-primary);
  box-shadow: 0 0 0 3px var(--mint-shadow);
}

.form-group textarea {
  resize: vertical;
  min-height: 120px;
}

.submit-btn {
  background: linear-gradient(135deg, var(--mint-primary) 0%, var(--mint-dark) 100%);
  color: white;
  padding: 14px 28px;
  border-radius: 12px;
  font-size: 1rem;
  font-weight: 600;
  display: inline-flex;
  align-items: center;
  gap: 10px;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  width: 100%;
  justify-content: center;
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px var(--mint-shadow-hover);
}

.faq-section {
  background: linear-gradient(145deg, var(--mint-pale) 0%, var(--mint-bg) 100%);
  border-radius: 18px;
  padding: 44px;
  border: 1px solid var(--mint-border);
=======
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
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
}

/* FAQ */
.faq-section h2 {
<<<<<<< HEAD
  color: var(--mint-text);
  margin-bottom: 25px;
  font-size: 1.5rem;
=======
  color: #4F6F52;
  margin-bottom: 20px;
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
  text-align: center;
}

.faq-list {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.faq-item {
<<<<<<< HEAD
  background: var(--mint-white);
  border-radius: 12px;
  margin-bottom: 12px;
  overflow: hidden;
  border: 1px solid var(--mint-border);
=======
  background: #ffffff; /* White background */
  padding: 15px;
  border-radius: 10px;
  border: 1px solid #8FBC8F;
  box-shadow: 0 3px 8px rgba(0,0,0,0.08);
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
}

.faq-question {
  display: flex;
  justify-content: space-between;
  cursor: pointer;
<<<<<<< HEAD
  color: var(--mint-text);
  font-weight: 500;
  transition: background-color 0.2s ease;
}

.faq-question:hover {
  background: var(--mint-bg);
}

.faq-question svg {
  color: var(--mint-primary);
  transition: transform 0.2s ease;
}

.faq-question svg.rotated {
  transform: rotate(180deg);
}

.faq-answer {
  padding: 0 20px 16px;
  color: var(--mint-text-muted);
  line-height: 1.6;
=======
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
>>>>>>> d992d96f276e221b0723eb068958f1f4b983d1f4
}
</style>
