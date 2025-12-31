<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-bottom">
        <p class="copyright">&copy; 2025 Gideon Gandoki. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: var(--neutral-900);
  color: var(--neutral-300);
  padding: var(--spacing-3xl) 0 var(--spacing-lg);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.footer-grid {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1fr;
  gap: var(--spacing-xl);
  margin-bottom: var(--spacing-xl);
}

.footer-section.brand {
  max-width: 350px;
}

.brand-name {
  font-size: 1.5rem;
  font-weight: 700;
  color: white;
  margin-bottom: var(--spacing-sm);
}

.brand-description {
  line-height: 1.5;
  margin-bottom: var(--spacing-md);
}

.social-links {
  display: flex;
  gap: var(--spacing-sm);
}

.social-link {
  width: 2.5rem;
  height: 2.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 0.5rem;
  color: var(--neutral-300);
  transition: all 0.2s ease;
}

.social-link:hover {
  background: var(--primary-600);
  color: white;
  transform: translateY(-2px);
}

.footer-heading {
  font-size: 0.875rem;
  font-weight: 600;
  color: white;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: var(--spacing-md);
}

.footer-links {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: var(--spacing-xs);
}

.footer-links a {
  color: var(--neutral-400);
  text-decoration: none;
  transition: color 0.2s ease;
}

.footer-links a:hover {
  color: white;
}

.footer-bottom {
  padding-top: var(--spacing-xl);
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  text-align: center;
}

.copyright {
  color: var(--neutral-500);
  font-size: 0.875rem;
}

@media (max-width: 968px) {
  .footer-grid {
    grid-template-columns: 1fr 1fr;
    gap: var(--spacing-2xl);
  }

  .footer-section.brand {
    grid-column: 1 / -1;
    max-width: 100%;
  }
}

@media (max-width: 640px) {
  .footer-grid {
    grid-template-columns: 1fr;
    gap: var(--spacing-xl);
  }
}
</style>
