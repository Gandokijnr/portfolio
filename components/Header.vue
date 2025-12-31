<template>
  <header class="header" :class="{ 'scrolled': isScrolled }">
    <div class="container">
      <div class="logo">
        <span class="logo-text">Gideon</span>
      </div>

      <nav class="nav">
        <a href="#about" class="nav-link">About</a>
        <a href="#projects" class="nav-link">Projects</a>
        <a href="#contact" class="nav-link">Contact</a>
      </nav>

      <div class="actions">
        <a href="#projects" class="btn btn-secondary">View projects</a>
        <a href="#contact" class="btn btn-primary">Contact me</a>
      </div>

      <button class="mobile-menu" @click="toggleMenu">
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>

    <div class="mobile-nav" :class="{ 'open': menuOpen }">
      <a href="#about" class="mobile-nav-link" @click="toggleMenu">About</a>
      <a href="#projects" class="mobile-nav-link" @click="toggleMenu">Projects</a>
      <a href="#contact" class="mobile-nav-link" @click="toggleMenu">Contact</a>
      <div class="mobile-actions">
        <a href="#projects" class="btn btn-secondary" @click="toggleMenu">View projects</a>
        <a href="#contact" class="btn btn-primary" @click="toggleMenu">Contact me</a>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const isScrolled = ref(false);
const menuOpen = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 20;
};

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value;
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: var(--spacing-md) 0;
  transition: all 0.3s ease;
  background: rgba(15, 23, 42, 0.9);
  backdrop-filter: blur(18px);
  border-bottom: 1px solid rgba(148, 163, 184, 0.4);
}

.header.scrolled {
  background: rgba(15, 23, 42, 0.98);
  box-shadow: 0 10px 30px rgba(15, 23, 42, 0.8);
  padding: var(--spacing-sm) 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo-text {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--neutral-50);
}

.nav {
  display: flex;
  gap: var(--spacing-lg);
}

.nav-link {
  color: var(--neutral-300);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.2s ease;
}

.nav-link:hover {
  color: var(--primary-300);
}

.actions {
  display: flex;
  gap: var(--spacing-sm);
}

.btn {
  padding: 0.625rem 1.5rem;
  border-radius: 0.5rem;
  font-weight: 600;
  font-size: 0.875rem;
  cursor: pointer;
  transition: all 0.2s ease;
  border: 1px solid transparent;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  white-space: nowrap;
}

.btn-primary {
  background: var(--primary-600);
  color: white;
}

.btn-primary:hover {
  background: var(--primary-700);
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(2, 132, 199, 0.3);
}

.btn-secondary {
  background: transparent;
  color: var(--neutral-100);
  border: 1px solid rgba(148, 163, 184, 0.6);
}

.btn-secondary:hover {
  background: rgba(15, 23, 42, 0.9);
  border-color: var(--primary-500);
}

.mobile-menu {
  display: none;
  flex-direction: column;
  gap: 0.25rem;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
}

.mobile-menu span {
  width: 1.5rem;
  height: 2px;
  background: var(--neutral-200);
  transition: all 0.3s ease;
}

.mobile-nav {
  display: none;
  position: fixed;
  top: 5rem;
  left: 0;
  right: 0;
  background: rgba(15, 23, 42, 0.98);
  padding: var(--spacing-md);
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transform: translateY(-100%);
  opacity: 0;
  transition: all 0.3s ease;
}

.mobile-nav.open {
  transform: translateY(0);
  opacity: 1;
}

.mobile-nav-link {
  display: block;
  padding: var(--spacing-sm);
  color: var(--neutral-200);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.2s ease;
}

.mobile-nav-link:hover {
  color: var(--primary-300);
}

.mobile-actions {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-sm);
  margin-top: var(--spacing-md);
}

.mobile-actions .btn {
  width: 100%;
}

@media (max-width: 768px) {
  .nav,
  .actions {
    display: none;
  }

  .mobile-menu {
    display: flex;
  }

  .mobile-nav {
    display: block;
  }
}
</style>
