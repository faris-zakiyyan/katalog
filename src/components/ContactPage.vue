<template>
  <div class="contact-container">
    <h2>GET IN TOUCH</h2>
    <p class="subtitle">For inquiries, support, or order tracking, send us a message below.</p>

    <form @submit.prevent="handleSubmit" class="contact-form">
      <div class="form-group">
        <label for="name">NAME</label>
        <input type="text" id="name" v-model="formData.name" placeholder="Your name" required />
      </div>

      <div class="form-group">
        <label for="email">EMAIL</label>
        <input type="email" id="email" v-model="formData.email" placeholder="your@email.com" required />
      </div>

      <div class="form-group">
        <label for="message">MESSAGE</label>
        <textarea id="message" v-model="formData.message" rows="5" placeholder="Write your message here..." required></textarea>
      </div>

      <button type="submit" class="btn-send">SEND MESSAGE</button>

    </form>
  </div>
  <div class="info-item">
          <div>
            <strong>contact</strong>
            <p>0895 6058 66615</p>
          </div>
          <div>
            <strong>email</strong>
            <p>buniiversity@gmail.com</p>
        </div>
        </div>
</template>

<script setup>
import { reactive } from 'vue'

const formData = reactive({
  name: '',
  email: '',
  message: ''
})

const handleSubmit = () => {
  alert(`Thank you ${formData.name}! Your message has been sent successfully.`)
  formData.name = ''
  formData.email = ''
  formData.message = ''
}
</script>

<style scoped>
.contact-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 1rem 0;
}

h2 {
  font-size: 1.5rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 0.5rem;
  text-align: center;
}

.subtitle {
  color: #888888;
  font-size: 0.85rem;
  text-align: center;
  margin-bottom: 2rem;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

label {
  font-size: 0.75rem;
  letter-spacing: 1px;
  color: #aaaaaa;
}

input, textarea {
  background-color: #1a1a1a;
  border: 1px solid #333333;
  color: #ffffff;
  padding: 0.8rem;
  font-size: 0.9rem;
  border-radius: 2px;
  outline: none;
  transition: border-color 0.2s ease;
}

input:focus, textarea:focus {
  border-color: #ffffff;
}

.btn-send {
  padding: 0.85rem;
  background-color: #ffffff;
  color: #000000;
  border: none;
  font-weight: 700;
  font-size: 0.75rem;
  letter-spacing: 1.5px;
  cursor: pointer;
  text-transform: uppercase;
  transition: background-color 0.2s ease;
  margin-top: 0.5rem;
}

.btn-send:hover {
  background-color: #cccccc;
}
</style>