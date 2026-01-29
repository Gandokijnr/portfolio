<template>
  <section id="about" class="hero">
    <div class="container">
      <div class="content">
        <div class="greeting">
          <span class="wave">👋</span>
          <span class="greeting-text">Hello, I'm</span>
        </div>
        <h1 class="title">Gideon</h1>
        <p class="role">Web Developer & UI Designer</p>
        <p class="subtitle">
          I craft modern, responsive web applications with a focus on intuitive design 
          and exceptional user experiences. Specializing in Vue/Nuxt, React, Python, 
          and Node.js to bring ideas to life.
        </p>
        
        <div class="cta-buttons">
          <a href="#projects" class="btn btn-primary">
            <span>View My Work</span>
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none">
              <path d="M7 10L13 10M13 10L10 7M13 10L10 13" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </a>
          <a href="#contact" class="btn btn-secondary">
            <span>Get In Touch</span>
          </a>
        </div>

        <div class="stats">
          <div class="stat-item">
            <div class="stat-number">10+</div>
            <div class="stat-label">Projects Delivered</div>
          </div>
          <div class="stat-divider"></div>
          <div class="stat-item">
            <div class="stat-number">3+</div>
            <div class="stat-label">Years Experience</div>
          </div>
          <div class="stat-divider"></div>
          <div class="stat-item">
            <div class="stat-number">100%</div>
            <div class="stat-label">Client Satisfaction</div>
          </div>
        </div>

        <div class="tech-stack">
          <span class="tech-label">Tech Stack:</span>
          <div class="tech-badges">
            <span class="tech-badge">Vue.js</span>
            <span class="tech-badge">Nuxt</span>
            <span class="tech-badge">TypeScript</span>
            <span class="tech-badge">React</span>
            <span class="tech-badge">Python</span>
          </div>
        </div>
      </div>

      <div class="visual">
        <div class="image-wrapper">
          <div class="glow-effect"></div>
          <img
            src="https://res.cloudinary.com/dqqycsgmn/image/upload/v1757150936/ea52cef7-48ae-4f4e-9376-0d76275ea776.png"
            alt="Gideon - web developer"
            class="hero-image"
          />
          <div class="floating-badge badge-1">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
              <path d="M12 2L15.09 8.26L22 9.27L17 14.14L18.18 21.02L12 17.77L5.82 21.02L7 14.14L2 9.27L8.91 8.26L12 2Z" fill="currentColor"/>
            </svg>
            <span>Quality Code</span>
          </div>
          <div class="floating-badge badge-2">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
              <path d="M13 2L3 14H12L11 22L21 10H12L13 2Z" fill="currentColor"/>
            </svg>
            <span>Fast Delivery</span>
          </div>
        </div>
      </div>
    </div>

    <div class="scroll-indicator">
      <div class="scroll-text">Scroll to explore</div>
      <div class="scroll-arrow">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
          <path d="M12 5V19M12 19L5 12M12 19L19 12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding: 6rem 0 4rem;
  background: 
    radial-gradient(circle at 20% 20%, rgba(99, 102, 241, 0.08) 0%, transparent 50%),
    radial-gradient(circle at 80% 80%, rgba(239, 68, 68, 0.06) 0%, transparent 50%),
    linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #0f172a 100%);
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(99, 102, 241, 0.5), transparent);
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 2rem;
  display: grid;
  grid-template-columns: 1.1fr 0.9fr;
  gap: 4rem;
  align-items: center;
  position: relative;
  z-index: 1;
}

.content {
  max-width: 640px;
}

.greeting {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 1rem;
  animation: fade-in-up 0.6s ease-out;
}

.wave {
  font-size: 2rem;
  display: inline-block;
  animation: wave 2.5s ease-in-out infinite;
  transform-origin: 70% 70%;
}

@keyframes wave {
  0%, 100% { transform: rotate(0deg); }
  10%, 30% { transform: rotate(14deg); }
  20%, 40% { transform: rotate(-8deg); }
  50% { transform: rotate(0deg); }
}

.greeting-text {
  font-size: 1.125rem;
  color: var(--neutral-400);
  font-weight: 500;
}

.title {
  font-size: clamp(3.5rem, 8vw, 5.5rem);
  font-weight: 800;
  background: linear-gradient(135deg, #f8fafc 0%, #cbd5e1 100%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  line-height: 1;
  margin-bottom: 0.5rem;
  letter-spacing: -0.04em;
  animation: fade-in-up 0.6s ease-out 0.1s backwards;
}

.role {
  font-size: 1.5rem;
  color: var(--primary-400);
  font-weight: 600;
  margin-bottom: 1.5rem;
  animation: fade-in-up 0.6s ease-out 0.2s backwards;
}

.subtitle {
  font-size: 1.125rem;
  line-height: 1.7;
  color: var(--neutral-300);
  margin-bottom: 2.5rem;
  animation: fade-in-up 0.6s ease-out 0.3s backwards;
}

.cta-buttons {
  display: flex;
  gap: 1rem;
  margin-bottom: 3rem;
  animation: fade-in-up 0.6s ease-out 0.4s backwards;
}

.btn {
  padding: 1rem 2rem;
  border-radius: 0.75rem;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  border: none;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  position: relative;
  overflow: hidden;
}

.btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
  transition: left 0.5s ease;
}

.btn:hover::before {
  left: 100%;
}

.btn-primary {
  background: linear-gradient(135deg, var(--primary-600) 0%, var(--primary-700) 100%);
  color: white;
  box-shadow: 0 4px 20px rgba(59, 130, 246, 0.3);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 30px rgba(59, 130, 246, 0.4);
}

.btn-primary svg {
  transition: transform 0.3s ease;
}

.btn-primary:hover svg {
  transform: translateX(4px);
}

.btn-secondary {
  background: rgba(15, 23, 42, 0.6);
  color: var(--neutral-100);
  border: 1.5px solid rgba(148, 163, 184, 0.3);
  backdrop-filter: blur(10px);
}

.btn-secondary:hover {
  background: rgba(15, 23, 42, 0.8);
  border-color: var(--primary-400);
  transform: translateY(-2px);
  box-shadow: 0 4px 20px rgba(59, 130, 246, 0.2);
}

.stats {
  display: flex;
  align-items: center;
  gap: 2rem;
  padding: 1.5rem 0;
  border-top: 1px solid rgba(148, 163, 184, 0.1);
  border-bottom: 1px solid rgba(148, 163, 184, 0.1);
  margin-bottom: 2rem;
  animation: fade-in-up 0.6s ease-out 0.5s backwards;
}

.stat-item {
  text-align: center;
}

.stat-number {
  font-size: 2rem;
  font-weight: 700;
  background: linear-gradient(135deg, var(--primary-400) 0%, var(--primary-600) 100%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  line-height: 1.2;
  margin-bottom: 0.25rem;
}

.stat-label {
  font-size: 0.875rem;
  color: var(--neutral-400);
  font-weight: 500;
}

.stat-divider {
  width: 1px;
  height: 40px;
  background: linear-gradient(to bottom, transparent, rgba(148, 163, 184, 0.3), transparent);
}

.tech-stack {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  animation: fade-in-up 0.6s ease-out 0.6s backwards;
}

.tech-label {
  font-size: 0.875rem;
  color: var(--neutral-400);
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.tech-badges {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.tech-badge {
  padding: 0.5rem 1rem;
  background: rgba(59, 130, 246, 0.1);
  border: 1px solid rgba(59, 130, 246, 0.3);
  border-radius: 2rem;
  font-size: 0.875rem;
  color: var(--primary-300);
  font-weight: 500;
  transition: all 0.3s ease;
}

.tech-badge:hover {
  background: rgba(59, 130, 246, 0.2);
  border-color: var(--primary-400);
  transform: translateY(-2px);
}

.visual {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  animation: fade-in-scale 0.8s ease-out 0.4s backwards;
}

.image-wrapper {
  position: relative;
  width: 100%;
  max-width: 500px;
}

.glow-effect {
  position: absolute;
  inset: -20%;
  background: radial-gradient(circle, rgba(59, 130, 246, 0.3) 0%, transparent 70%);
  filter: blur(60px);
  animation: pulse-glow 4s ease-in-out infinite;
  z-index: 0;
}

@keyframes pulse-glow {
  0%, 100% { opacity: 0.5; transform: scale(1); }
  50% { opacity: 0.8; transform: scale(1.1); }
}

.hero-image {
  width: 100%;
  height: auto;
  display: block;
  border-radius: 1.5rem;
  position: relative;
  z-index: 1;
  box-shadow: 
    0 20px 60px rgba(0, 0, 0, 0.4),
    0 0 0 1px rgba(148, 163, 184, 0.1);
  transition: transform 0.5s cubic-bezier(0.4, 0, 0.2, 1);
}

.image-wrapper:hover .hero-image {
  transform: scale(1.02) translateY(-8px);
}

.floating-badge {
  position: absolute;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1.25rem;
  background: rgba(15, 23, 42, 0.95);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(148, 163, 184, 0.2);
  border-radius: 3rem;
  font-size: 0.875rem;
  font-weight: 600;
  color: var(--neutral-100);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
  z-index: 2;
  animation: float 3s ease-in-out infinite;
}

.floating-badge svg {
  width: 20px;
  height: 20px;
  color: var(--primary-400);
}

.badge-1 {
  top: 10%;
  right: -5%;
  animation-delay: 0s;
}

.badge-2 {
  bottom: 15%;
  left: -5%;
  animation-delay: 1.5s;
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-12px); }
}

.scroll-indicator {
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  animation: fade-in 1s ease-out 1s backwards;
}

.scroll-text {
  font-size: 0.75rem;
  color: var(--neutral-500);
  text-transform: uppercase;
  letter-spacing: 0.1em;
  font-weight: 600;
}

.scroll-arrow {
  color: var(--neutral-400);
  animation: bounce 2s ease-in-out infinite;
}

@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(8px); }
}

@keyframes fade-in-up {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fade-in-scale {
  from {
    opacity: 0;
    transform: scale(0.95);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

@keyframes fade-in {
  from { opacity: 0; }
  to { opacity: 1; }
}

@media (max-width: 1024px) {
  .container {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .visual {
    order: -1;
  }

  .content {
    max-width: 100%;
  }
}

@media (max-width: 768px) {
  .hero {
    padding: 5rem 0 3rem;
    min-height: auto;
  }

  .container {
    padding: 0 1.5rem;
  }

  .title {
    font-size: 3rem;
  }

  .role {
    font-size: 1.25rem;
  }

  .subtitle {
    font-size: 1rem;
  }

  .cta-buttons {
    flex-direction: column;
  }

  .btn {
    width: 100%;
    justify-content: center;
  }

  .stats {
    flex-wrap: wrap;
    gap: 1.5rem;
  }

  .stat-divider {
    display: none;
  }

  .stat-item {
    flex: 1;
    min-width: 120px;
  }

  .floating-badge {
    padding: 0.5rem 1rem;
    font-size: 0.75rem;
  }

  .scroll-indicator {
    display: none;
  }
}

@media (max-width: 480px) {
  .greeting {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.5rem;
  }

  .title {
    font-size: 2.5rem;
  }

  .stats {
    justify-content: space-between;
  }

  .stat-item {
    min-width: auto;
  }

  .stat-number {
    font-size: 1.5rem;
  }
}
</style>