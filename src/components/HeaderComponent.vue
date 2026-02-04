<template>
  <header class="header">
    <div class="header-content">
      <div class="brand">
        <div class="brand-icon">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="32" height="32">
            <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
          </svg>
        </div>
        <div class="brand-text">
          <h1>Academy Hub</h1>
          <p>Student Management System</p>
        </div>
      </div>
      <nav class="nav-menu">
        <router-link to="/" class="nav-item" active-class="active">
          <div class="nav-icon">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
              <path d="M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z"/>
            </svg>
          </div>
          <span class="nav-label">Dashboard</span>
        </router-link>
        <router-link to="/students" class="nav-item" active-class="active">
          <div class="nav-icon">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
              <path d="M16 11c1.66 0 2.99-1.34 2.99-3S17.66 5 16 5c-1.66 0-3 1.34-3 3s1.34 3 3 3zm-8 0c1.66 0 2.99-1.34 2.99-3S9.66 5 8 5C6.34 5 5 6.34 5 8s1.34 3 3 3zm0 2c-2.33 0-7 1.17-7 3.5V19h14v-2.5c0-2.33-4.67-3.5-7-3.5zm8 0c-.29 0-.62.02-.97.05 1.16.84 1.97 1.97 1.97 3.45V19h6v-2.5c0-2.33-4.67-3.5-7-3.5z"/>
            </svg>
          </div>
          <span class="nav-label">Students</span>
        </router-link>
        <router-link to="/about" class="nav-item" active-class="active">
          <div class="nav-icon">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
              <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 15h-2v-6h2v6zm0-8h-2V7h2v2z"/>
            </svg>
          </div>
          <span class="nav-label">About</span>
        </router-link>
        <router-link to="/contact" class="nav-item" active-class="active">
          <span class="nav-label">Contact</span>
        </router-link>
      </nav>
      <div class="user-actions">
        <button class="action-btn">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" width="20" height="20">
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 3c1.66 0 3 1.34 3 3s-1.34 3-3 3-3-1.34-3-3 1.34-3 3-3zm0 14.2c-2.5 0-4.71-1.28-6-3.22.03-1.99 4-3.08 6-3.08 1.99 0 5.97 1.09 6 3.08-1.29 1.94-3.5 3.22-6 3.22z"/>
          </svg>
        </button>
      </div>
    </div>
  </header>
</template>

<script setup>
// HeaderComponent - Main navigation header
// This component provides navigation links to different pages
</script>

.header {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.2);
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
  z-index: 100;
}
=======
.header {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.2);
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
  z-index: 100;
}
=======
  background: linear-gradient(
    135deg,
    #6B8E23 0%,   /* olive green */
    #8FBC8F 50%,  /* soft green */
    #CDE6C3 100%  /* light beige-green */
  );
  color: #F5F1E8; /* beige text */
  padding: 0 20px;
  box-shadow: 0 2px 10px rgba(107, 142, 35, 0.25);
>>>>>>> fc77fd55412f11c84ae2adc62ce4f65a5ccd1541
}

.header-content {
  max-width: 1400px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 2rem;
}

.brand {
  display: flex;
  align-items: center;
<<<<<<< HEAD
  gap: 1rem;
}

.brand-icon {
  color: #667eea;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 12px;
  padding: 0.5rem;
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);
=======
  gap: 10px;
  font-weight: bold;
  font-size: 1.2rem;
  color: #F5F1E8;
}

.logo-icon {
  color: #F5F1E8;
>>>>>>> fc77fd55412f11c84ae2adc62ce4f65a5ccd1541
}

.brand-text h1 {
  font-size: 1.5rem;
  font-weight: 700;
  color: #2d3748;
  margin: 0;
}

.brand-text p {
  font-size: 0.875rem;
  color: #718096;
  margin: 0;
}

.nav-menu {
  display: flex;
  gap: 2rem;
}

<<<<<<< HEAD
.nav-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.25rem;
  padding: 0.75rem 1rem;
  border-radius: 12px;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  text-decoration: none;
  color: #4a5568;
  position: relative;
  overflow: hidden;
}

.nav-item::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
  opacity: 0;
  transition: opacity 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  border-radius: 12px;
}

.nav-item:hover::before,
.nav-item.active::before {
  opacity: 1;
}

.nav-item:hover,
.nav-item.active {
  color: #667eea;
  transform: translateY(-3px) scale(1.05);
}

.nav-icon {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  z-index: 1;
}

.nav-item:hover .nav-icon,
.nav-item.active .nav-icon {
  transform: scale(1.15) rotate(5deg);
}

.nav-label {
  font-size: 0.875rem;
  font-weight: 500;
  position: relative;
  z-index: 1;
}

.nav-label {
  font-size: 0.875rem;
  font-weight: 500;
}

.user-actions {
=======
.nav-link {
  color: #F5F1E8;
  padding: 8px 16px;
  border-radius: 5px;
  transition: background-color 0.3s ease;
>>>>>>> fc77fd55412f11c84ae2adc62ce4f65a5ccd1541
  display: flex;
  align-items: center;
}

<<<<<<< HEAD
.action-btn {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border: none;
  border-radius: 50%;
  width: 48px;
  height: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);
}

.action-btn:hover {
  transform: scale(1.05);
  box-shadow: 0 6px 20px rgba(102, 126, 234, 0.4);
=======
.nav-link:hover,
.nav-link.router-link-active {
  background-color: rgba(245, 241, 232, 0.35); /* beige hover */
  color: #556B2F; /* darker green text */
>>>>>>> fc77fd55412f11c84ae2adc62ce4f65a5ccd1541
}

</style>
