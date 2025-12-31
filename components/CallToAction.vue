<template>
  <section id="contact" class="cta">
    <div class="container">
      <div class="content">
        <h2 class="title">Let's work together</h2>
        <p class="subtitle">
          Have a project in mind or want to collaborate? Feel free to reach out.
        </p>
        <div class="buttons">
          <a href="mailto:abahgideon111@gmail.com" class="btn btn-primary">Email me</a>
          <a href="https://github.com/Gandokijnr" class="btn btn-secondary" target="_blank" rel="noopener noreferrer">GitHub</a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.cta {
  padding: var(--spacing-3xl) 0;
  background: linear-gradient(135deg, var(--primary-600) 0%, var(--primary-700) 100%);
  position: relative;
  overflow: hidden;
}

.cta::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -10%;
  width: 500px;
  height: 500px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
}

.cta::after {
  content: '';
  position: absolute;
  bottom: -30%;
  left: -5%;
  width: 400px;
  height: 400px;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 50%;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
  position: relative;
  z-index: 1;
}

.content {
  text-align: center;
  max-width: 700px;
  margin: 0 auto;
}

.title {
  font-size: 2.5rem;
  color: white;
  margin-bottom: var(--spacing-md);
}

.subtitle {
  font-size: 1.25rem;
  color: rgba(255, 255, 255, 0.9);
  margin-bottom: var(--spacing-xl);
  line-height: 1.5;
}

.buttons {
  display: flex;
  gap: var(--spacing-sm);
  justify-content: center;
}

.btn {
  padding: 1rem 2rem;
  border-radius: 0.5rem;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.2s ease;
  border: none;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.btn-primary {
  background: white;
  color: var(--primary-700);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

.btn-secondary {
  background: rgba(255, 255, 255, 0.1);
  color: white;
  border: 2px solid white;
  backdrop-filter: blur(10px);
}

.btn-secondary:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: translateY(-2px);
}

@media (max-width: 640px) {
  .title {
    font-size: 2rem;
  }

  .subtitle {
    font-size: 1rem;
  }

  .buttons {
    flex-direction: column;
  }

  .buttons .btn {
    width: 100%;
  }
}
</style>
