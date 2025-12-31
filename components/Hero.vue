<template>
  <section id="about" class="hero">
    <div class="container">
      <div class="content">
        <div class="badge">Web Developer / Portfolio</div>
        <h1 class="title">Hi, I'm Gideon</h1>
        <p class="subtitle">
          I build modern, responsive web applications focused on clean design,
          great user experience, and solid performance with Vue/Nuxt, React, Python, Node.js, and more. This site showcases a
          selection of my recent work.
        </p>
        <div class="cta-buttons">
          <a href="#projects" class="btn btn-primary btn-large">View Projects</a>
          <a href="#contact" class="btn btn-secondary btn-large">Contact Me</a>
        </div>
        <div class="stats">
          <div class="stat">
            <div class="stat-label">Primary focus</div>
            <div class="stat-value">Web applications</div>
          </div>
          <div class="stat">
            <div class="stat-label">Tech stack</div>
            <div class="stat-value">Vue / Nuxt / TypeScript</div>
          </div>
          <div class="stat">
            <div class="stat-label">Projects</div>
            <div class="stat-value">10+</div>
          </div>
        </div>
      </div>
      <div class="visual">
        <div class="placeholder-image">
          <img
            src="https://res.cloudinary.com/dqqycsgmn/image/upload/v1757150936/ea52cef7-48ae-4f4e-9376-0d76275ea776.png"
            alt="Gideon - web developer hero visual"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  padding: calc(var(--spacing-3xl) + 4rem) 0 var(--spacing-3xl);
  background:
    radial-gradient(circle at top left, rgba(56, 189, 248, 0.25), transparent 55%),
    radial-gradient(circle at top right, rgba(37, 99, 235, 0.18), transparent 55%),
    linear-gradient(180deg, var(--neutral-950) 0%, var(--neutral-900) 100%);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-3xl);
  align-items: center;
}

.content {
  max-width: 600px;
}

.badge {
  display: inline-block;
  padding: 0.5rem 1rem;
  background: rgba(15, 23, 42, 0.9);
  color: var(--primary-100);
  border-radius: 2rem;
  font-size: 0.875rem;
  font-weight: 600;
  margin-bottom: var(--spacing-md);
  border: 1px solid rgba(148, 163, 184, 0.4);
}

.title {
  font-size: 3.5rem;
  margin-bottom: var(--spacing-md);
  color: var(--neutral-50);
  letter-spacing: -0.02em;
}

.subtitle {
  font-size: 1.25rem;
  color: var(--neutral-300);
  margin-bottom: var(--spacing-xl);
  line-height: 1.5;
}

.cta-buttons {
  display: flex;
  gap: var(--spacing-sm);
  margin-bottom: var(--spacing-3xl);
}

.btn {
  padding: 0.625rem 1.5rem;
  border-radius: 0.5rem;
  font-weight: 600;
  font-size: 0.875rem;
  cursor: pointer;
  transition: all 0.2s ease;
  border: none;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.btn-large {
  padding: 1rem 2rem;
  font-size: 1rem;
}

.btn-primary {
  background: var(--primary-600);
  color: white;
}

.btn-primary:hover {
  background: var(--primary-700);
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(2, 132, 199, 0.3);
}

.btn-secondary {
  background: transparent;
  color: var(--neutral-100);
  border: 1px solid rgba(148, 163, 184, 0.5);
}

.btn-secondary:hover {
  background: rgba(15, 23, 42, 0.9);
  border-color: var(--primary-500);
  transform: translateY(-2px);
  box-shadow: 0 4px 20px rgba(15, 23, 42, 0.6);
}

.stats {
  display: flex;
  gap: var(--spacing-xl);
}

.stat {
  text-align: left;
}

.stat-value {
  font-size: 2rem;
  font-weight: 700;
  color: var(--neutral-50);
  margin-bottom: 0.25rem;
}

.stat-label {
  font-size: 0.875rem;
  color: var(--neutral-400);
}

.visual {
  display: flex;
  justify-content: center;
  align-items: center;
}

.placeholder-image {
  width: 100%;
  max-width: 500px;
  border-radius: 1rem;
  overflow: hidden;
  box-shadow: 0 24px 60px rgba(15, 23, 42, 0.8);
  transition: transform 0.3s ease;
}

.placeholder-image:hover {
  transform: translateY(-8px);
}

.placeholder-image svg {
  width: 100%;
  height: auto;
  display: block;
}

.placeholder-image img {
  width: 100%;
  height: auto;
  display: block;
}

@media (max-width: 968px) {
  .container {
    grid-template-columns: 1fr;
    gap: var(--spacing-2xl);
  }

  .title {
    font-size: 2.5rem;
  }

  .visual {
    order: -1;
  }
}

@media (max-width: 640px) {
  .hero {
    padding: calc(var(--spacing-2xl) + 4rem) 0 var(--spacing-2xl);
  }

  .title {
    font-size: 2rem;
  }

  .subtitle {
    font-size: 1rem;
  }

  .cta-buttons {
    flex-direction: column;
  }

  .cta-buttons .btn {
    width: 100%;
  }

  .stats {
    flex-direction: column;
    gap: var(--spacing-md);
  }
}
</style>
