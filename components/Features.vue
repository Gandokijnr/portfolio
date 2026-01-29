<template>
  <section id="projects" class="projects">
    <div class="container">
      <div class="section-header">
        <div class="header-content">
          <span class="section-badge">Portfolio</span>
          <h2 class="section-title">Featured Projects</h2>
          <p class="section-subtitle">
            Explore a curated selection of web applications I've designed and built, 
            from e-commerce platforms to SaaS solutions.
          </p>
        </div>
        
        <div class="filter-tabs">
          <button 
            v-for="category in categories" 
            :key="category"
            :class="['filter-tab', { active: activeCategory === category }]"
            @click="activeCategory = category"
          >
            {{ category }}
            <span class="count">{{ getProjectCount(category) }}</span>
          </button>
        </div>
      </div>

      <div class="features-grid">
        <div 
          v-for="(feature, index) in filteredFeatures" 
          :key="feature.title"
          class="feature-card"
          :style="{ animationDelay: `${index * 0.1}s` }"
        >
          <div class="card-image">
            <div class="icon" v-html="feature.icon"></div>
            <div class="card-overlay">
              <button 
                v-if="feature.problem || feature.who || feature.impact"
                type="button"
                class="quick-view-btn"
                @click="openFeature(feature)"
              >
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                  <path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"/>
                  <circle cx="12" cy="12" r="3"/>
                </svg>
                Quick View
              </button>
            </div>
          </div>

          <div class="card-content">
            <div class="card-header">
              <h3 class="feature-title">{{ feature.title }}</h3>
              <span v-if="feature.year" class="year-badge">{{ feature.year }}</span>
            </div>
            
            <div v-if="feature.tags" class="tech-tags">
              <span v-for="tag in feature.tags" :key="tag" class="tech-tag">{{ tag }}</span>
            </div>
            
            <p class="feature-description">{{ feature.description }}</p>
            
            <div class="card-footer">
              <div class="feature-links">
                <a
                  v-if="feature.liveUrl"
                  :href="feature.liveUrl"
                  class="link-btn link-primary"
                  target="_blank"
                  rel="noopener noreferrer"
                  @click.stop
                >
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/>
                    <polyline points="15 3 21 3 21 9"/>
                    <line x1="10" y1="14" x2="21" y2="3"/>
                  </svg>
                  Live Site
                </a>
                <a
                  v-if="feature.codeUrl"
                  :href="feature.codeUrl"
                  class="link-btn link-secondary"
                  target="_blank"
                  rel="noopener noreferrer"
                  @click.stop
                >
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <polyline points="16 18 22 12 16 6"/>
                    <polyline points="8 6 2 12 8 18"/>
                  </svg>
                  Code
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div v-if="filteredFeatures.length === 0" class="empty-state">
        <svg width="64" height="64" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
          <circle cx="11" cy="11" r="8"/>
          <path d="m21 21-4.35-4.35"/>
        </svg>
        <p>No projects found in this category</p>
      </div>
    </div>

    <Teleport to="body">
      <Transition name="modal">
        <div v-if="selectedFeature" class="modal-backdrop" @click.self="closeModal">
          <div class="modal" @click.stop>
            <button type="button" class="modal-close" @click="closeModal">
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <line x1="18" y1="6" x2="6" y2="18"/>
                <line x1="6" y1="6" x2="18" y2="18"/>
              </svg>
            </button>

            <div class="modal-hero">
              <div class="modal-icon" v-html="selectedFeature.icon"></div>
              <div>
                <h3 class="modal-title">{{ selectedFeature.title }}</h3>
                <p v-if="selectedFeature.meta" class="modal-meta">{{ selectedFeature.meta }}</p>
              </div>
            </div>

            <p class="modal-description">{{ selectedFeature.description }}</p>

            <div 
              v-if="selectedFeature.problem || selectedFeature.who || selectedFeature.impact"
              class="modal-details"
            >
              <div v-if="selectedFeature.problem" class="detail-card">
                <div class="detail-icon">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <circle cx="12" cy="12" r="10"/>
                    <path d="M12 16v-4m0-4h.01"/>
                  </svg>
                </div>
                <div>
                  <h4 class="detail-title">The Problem</h4>
                  <p class="detail-text">{{ selectedFeature.problem }}</p>
                </div>
              </div>

              <div v-if="selectedFeature.who" class="detail-card">
                <div class="detail-icon">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/>
                    <circle cx="9" cy="7" r="4"/>
                    <path d="M23 21v-2a4 4 0 0 0-3-3.87"/>
                    <path d="M16 3.13a4 4 0 0 1 0 7.75"/>
                  </svg>
                </div>
                <div>
                  <h4 class="detail-title">Target Audience</h4>
                  <p class="detail-text">{{ selectedFeature.who }}</p>
                </div>
              </div>

              <div v-if="selectedFeature.impact" class="detail-card">
                <div class="detail-icon">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/>
                  </svg>
                </div>
                <div>
                  <h4 class="detail-title">Impact & Solution</h4>
                  <p class="detail-text">{{ selectedFeature.impact }}</p>
                </div>
              </div>
            </div>

            <div 
              v-if="selectedFeature.liveUrl || selectedFeature.codeUrl"
              class="modal-actions"
            >
              <a
                v-if="selectedFeature.liveUrl"
                :href="selectedFeature.liveUrl"
                class="modal-btn modal-btn-primary"
                target="_blank"
                rel="noopener noreferrer"
              >
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                  <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/>
                  <polyline points="15 3 21 3 21 9"/>
                  <line x1="10" y1="14" x2="21" y2="3"/>
                </svg>
                Visit Live Site
              </a>
              <a
                v-if="selectedFeature.codeUrl"
                :href="selectedFeature.codeUrl"
                class="modal-btn modal-btn-secondary"
                target="_blank"
                rel="noopener noreferrer"
              >
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                  <polyline points="16 18 22 12 16 6"/>
                  <polyline points="8 6 2 12 8 18"/>
                </svg>
                View Source Code
              </a>
            </div>
          </div>
        </div>
      </Transition>
    </Teleport>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue';

const categories = ['All Projects', 'E-commerce', 'SaaS', 'Web Apps', 'Landing Pages'];
const activeCategory = ref('All Projects');

const features = [
  {
    title: 'Selify',
    subtitle: 'Jiji.ng Alternative',
    year: '2023',
    category: 'E-commerce',
    tags: ['Vue.js', 'Node.js', 'MongoDB'],
    description:
      'A modern classifieds marketplace where users can quickly list items like phones, cars, electronics, and services with smart pricing suggestions and verified listings.',
    liveUrl: 'https://www.selify.ng',
    codeUrl: 'https://github.com/Gandokijnr',
    problem:
      'Informal, fragmented marketplaces make it hard for everyday buyers and sellers to discover trustworthy listings and complete secure transactions.',
    who:
      'Individual sellers and small merchants in Nigeria looking to buy and sell products safely online.',
    impact:
      'A modern, user-centric marketplace platform designed to make buying and selling simple, safe, and rewarding for everyone.',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h7l7 7-7 7-7-7z"/><circle cx="9" cy="7" r="1"/></svg>'
  },
  {
    title: 'VisionGardens Hotels',
    year: '2025',
    category: 'Web Apps',
    tags: ['Nuxt', 'TypeScript', 'Stripe'],
    description:
      'A luxury booking platform that transforms outdated hotel websites into a real-time, high-converting reservation experience.',
    problem:
      'Premium hotels struggle to present their value online and handle bookings smoothly due to clunky websites.',
    who:
      'Boutique and luxury hotel owners who want to attract high-value guests through a modern digital experience.',
    impact:
      'Combines elegant room showcases, real-time availability, and seamless reservations to increase direct bookings.',
    liveUrl: 'https://visiongardenshotel.com/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 10h18v8H3z"/><path d="M7 10V7a3 3 0 0 1 3-3h4a3 3 0 0 1 3 3v3"/></svg>'
  },
  {
    title: 'Roomio',
    year: '2025',
    category: 'SaaS',
    tags: ['Vue', 'Python', 'PostgreSQL'],
    description:
      'Transform hotel operations with effortless bookings, automated housekeeping, profit-driven revenue tools, and actionable analytics—all in one platform.',
    problem:
      'Hotels struggle with fragmented systems leading to errors, delays, staff stress, and lost revenue opportunities.',
    who:
      'Hotels, boutique stays, resorts, and serviced apartments looking to streamline operations and scale efficiently.',
    impact:
      'Centralizes availability, payments, and reservations to reduce admin overhead by 40% and deliver smoother guest experiences.',
    liveUrl: 'https://roommio.netlify.app/landing',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="4" y="4" width="9" height="14" rx="1"/><path d="M7 7h3M7 11h3M7 15h3"/><circle cx="18" cy="13" r="3"/></svg>'
  },
  {
    title: 'Winebay',
    year: '2025',
    category: 'E-commerce',
    tags: ['React', 'Commerce.js', 'Tailwind'],
    description:
      'A modern e-commerce experience for discovering and purchasing curated wines, combining rich product storytelling with smooth checkout.',
    problem:
      'Wine lovers and boutique brands struggle with fragmented shopping experiences that lack discovery tools and trust-building content.',
    who:
      'Wine enthusiasts, collectors, and boutique wine brands seeking better online shopping experiences.',
    impact:
      'Makes it easier to discover the right bottle and purchase with confidence through a polished, conversion-focused experience.',
    liveUrl: 'https://winebay.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M9 3h2v5a2 2 0 0 1-2 2v7"/><path d="M15 3h2v5a3 3 0 0 1-3 3h0a3 3 0 0 1-3-3V3h2"/></svg>'
  },
  {
    title: 'My UniCamp',
    year: '2025',
    category: 'Web Apps',
    tags: ['Vue', 'Algolia', 'Firebase'],
    description:
      'A course discovery platform that transforms scattered university information into a clear, searchable catalog of programs worldwide.',
    problem:
      'Prospective students are overwhelmed by scattered information and struggle to compare programs across schools.',
    who:
      'High school graduates, career switchers, and lifelong learners researching degree or certificate programs.',
    impact:
      'Simplifies program discovery, helping users quickly find relevant courses and make confident education decisions.',
    liveUrl: 'https://myunicamp.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 7l9-4 9 4-9 4-9-4z"/><path d="M7 10v5a5 5 0 0 0 10 0v-5"/></svg>'
  },
  {
    title: 'Farmxic',
    year: '2024',
    category: 'Web Apps',
    tags: ['Nuxt', 'Node.js', 'MongoDB'],
    description:
      'An agricultural platform connecting isolated farming efforts into an ecosystem of modern tools, knowledge, and market opportunities.',
    problem:
      'Small and mid-scale farmers lack access to modern techniques, reliable markets, and relevant agricultural information.',
    who:
      'Farmers and agricultural cooperatives seeking better tools, knowledge, and market connections.',
    impact:
      'Connects farmers to resources and market access, helping improve yields, income, and resilience.',
    liveUrl: 'https://www.farmxic.com/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 20c4-6 8-8 16-8-2.5 3-6 5-10 6.5"/><path d="M10 20c0-6 2-10 6-13"/></svg>'
  },
  {
    title: 'SurePicks',
    year: '2025',
    category: 'Web Apps',
    tags: ['React', 'Python', 'Redis'],
    description:
      'A sports prediction platform replacing gut-feel betting with data-driven insights and real-time odds analysis.',
    problem:
      'Sports bettors rely on guesswork or low-quality tips, resulting in uninformed bets and inconsistent outcomes.',
    who:
      'Recreational and semi-professional sports bettors seeking a data-backed edge.',
    impact:
      'Uses analytics, odds, and expert insights to help users make informed betting decisions and manage risk intelligently.',
    liveUrl: 'https://surepicks.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 19V9"/><path d="M9 19V5"/><path d="M14 19v-7"/><path d="M17 8l2 2 3-3"/></svg>'
  },
  {
    title: 'Real Estate Showcase',
    year: '2024',
    category: 'Landing Pages',
    tags: ['HTML', 'CSS', 'JavaScript'],
    description:
      'A modern listings interface transforming static property catalogs into a responsive, searchable home-hunting experience.',
    problem:
      'Homebuyers struggle to find relevant properties when listings are poorly presented or hard to search.',
    who:
      'Real estate agencies and property developers needing a modern online presence.',
    impact:
      'Makes properties easier to browse and filter, driving more qualified leads and higher engagement.',
    liveUrl: 'https://gidiestate.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 11l9-7 9 7v9a1 1 0 0 1-1 1h-5v-6H9v6H4a1 1 0 0 1-1-1z"/></svg>'
  },
  {
    title: 'Agency Aggregator',
    year: '2025',
    category: 'SaaS',
    tags: ['Vue', 'Laravel', 'MySQL'],
    description:
      'A management platform replacing scattered agency spreadsheets with a secure, all-in-one dashboard for teams, clients, and data.',
    problem:
      'Agencies manage clients and projects across disconnected tools, creating data silos and operational blind spots.',
    who:
      'Agency owners and operations managers at digital, creative, or marketing agencies.',
    impact:
      'Centralizes data with role-based access and dashboards, improving control, visibility, and efficiency.',
    liveUrl: 'https://agencyaggregator.netlify.app/auth/login',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16v4H4zM4 10h10v4H4zM4 16h7v4H4z"/></svg>'
  },
  {
    title: 'Fx Trading Academy',
    year: '2024',
    category: 'Web Apps',
    tags: ['Nuxt', 'Node.js', 'Chart.js'],
    description:
      'An educational platform transforming scattered forex knowledge into structured, actionable learning modules.',
    problem:
      'Aspiring traders face steep learning curves and fragmented resources, leading to costly mistakes in live markets.',
    who:
      'Beginner and intermediate forex traders seeking structured, practical learning.',
    impact:
      'Provides guided modules, analysis tools, and trading guides to reduce confusion and improve decision-making.',
    liveUrl: 'https://gandokigroup.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 20V10m4 10V6m4 14V8m4 12V4"/></svg>'
  },
  {
    title: 'Job Navigator',
    year: '2023',
    category: 'Web Apps',
    tags: ['React', 'Express', 'MongoDB'],
    description:
      'A job search platform transforming scattered applications into a single, trackable job-hunting workspace.',
    problem:
      'Job seekers waste time jumping between platforms and struggle to track applications effectively.',
    who:
      'Early- and mid-career professionals actively searching for new opportunities.',
    impact:
      'Consolidates listings, filters, and application tracking for a more focused, organized job search.',
    liveUrl: 'https://jobnavigator.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16v4H4zM4 10h12v4H4zM4 16h8v4H4z"/></svg>'
  },
  {
    title: 'Trade Ventures',
    year: '2023',
    category: 'E-commerce',
    tags: ['Vue', 'Stripe', 'PostgreSQL'],
    description:
      'A full-featured online store replacing basic catalogs with carts, payments, inventory control, and admin dashboards.',
    problem:
      'Product-based businesses lack robust storefronts with inventory management, payments, and admin tooling.',
    who:
      'Small and medium retailers looking to launch or upgrade their online sales channel.',
    impact:
      'Provides a complete buying experience and back-office tools, increasing sales while simplifying operations.',
    liveUrl: 'https://tradeventures.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M6 6h15l-1.5 9h-12z"/><circle cx="9" cy="19" r="1.5"/><circle cx="18" cy="19" r="1.5"/></svg>'
  },
  {
    title: 'Smart Calculator',
    year: '2023',
    category: 'Web Apps',
    tags: ['JavaScript', 'CSS', 'HTML'],
    description:
      'A modern browser-based calculator with advanced functions and history tracking for fast, traceable calculations.',
    problem:
      'Users rely on basic tools that lack advanced functions or history, making it easy to repeat work or make errors.',
    who:
      'Students, analysts, and professionals doing frequent ad-hoc calculations.',
    impact:
      "Advanced functions and history tracking speed up calculations and reduce mistakes.",
    liveUrl: 'https://caluculatingapp.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="4" y="3" width="16" height="18" rx="2"/><path d="M8 8h8M8 12h2m4 0h2M8 16h2m4 0h2"/></svg>'
  }
];

const selectedFeature = ref(null);

const filteredFeatures = computed(() => {
  if (activeCategory.value === 'All Projects') {
    return features;
  }
  return features.filter(f => f.category === activeCategory.value);
});

const getProjectCount = (category) => {
  if (category === 'All Projects') return features.length;
  return features.filter(f => f.category === category).length;
};

const openFeature = (feature) => {
  selectedFeature.value = feature;
  document.body.style.overflow = 'hidden';
};

const closeModal = () => {
  selectedFeature.value = null;
  document.body.style.overflow = '';
};
</script>

<style scoped>
.projects {
  position: relative;
  padding: 6rem 0;
  background: 
    radial-gradient(circle at 10% 20%, rgba(99, 102, 241, 0.05) 0%, transparent 50%),
    radial-gradient(circle at 90% 80%, rgba(239, 68, 68, 0.04) 0%, transparent 50%),
    linear-gradient(180deg, #0f172a 0%, #1e293b 50%, #0f172a 100%);
  overflow: hidden;
}

.container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 2rem;
}

.section-header {
  margin-bottom: 4rem;
}

.header-content {
  max-width: 700px;
  margin-bottom: 3rem;
}

.section-badge {
  display: inline-block;
  padding: 0.5rem 1rem;
  background: rgba(59, 130, 246, 0.1);
  border: 1px solid rgba(59, 130, 246, 0.3);
  border-radius: 2rem;
  font-size: 0.875rem;
  color: var(--primary-300);
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 1rem;
}

.section-title {
  font-size: clamp(2.5rem, 5vw, 3.5rem);
  font-weight: 800;
  color: var(--neutral-50);
  margin-bottom: 1rem;
  letter-spacing: -0.02em;
}

.section-subtitle {
  font-size: 1.125rem;
  color: var(--neutral-400);
  line-height: 1.6;
}

.filter-tabs {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
  padding: 0.5rem;
  background: rgba(15, 23, 42, 0.5);
  border-radius: 1rem;
  border: 1px solid rgba(148, 163, 184, 0.1);
  backdrop-filter: blur(10px);
  width: fit-content;
}

.filter-tab {
  padding: 0.75rem 1.5rem;
  border: none;
  background: transparent;
  color: var(--neutral-400);
  font-size: 0.9375rem;
  font-weight: 600;
  border-radius: 0.625rem;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.filter-tab:hover {
  color: var(--neutral-200);
  background: rgba(148, 163, 184, 0.05);
}

.filter-tab.active {
  background: var(--primary-600);
  color: white;
}

.count {
  padding: 0.125rem 0.5rem;
  background: rgba(255, 255, 255, 0.15);
  border-radius: 1rem;
  font-size: 0.75rem;
  font-weight: 700;
}

.filter-tab.active .count {
  background: rgba(255, 255, 255, 0.25);
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
  gap: 2rem;
}

.feature-card {
  position: relative;
  background: rgba(15, 23, 42, 0.6);
  border: 1px solid rgba(148, 163, 184, 0.1);
  border-radius: 1.5rem;
  overflow: hidden;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  opacity: 0;
  animation: fade-in-up 0.6s ease-out forwards;
}

@keyframes fade-in-up {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.feature-card:hover {
  transform: translateY(-8px);
  border-color: var(--primary-400);
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.4);
}

.card-image {
  position: relative;
  height: 200px;
  background: linear-gradient(135deg, rgba(59, 130, 246, 0.1) 0%, rgba(99, 102, 241, 0.05) 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.card-image::before {
  content: '';
  position: absolute;
  inset: 0;
  background: 
    radial-gradient(circle at 30% 30%, rgba(59, 130, 246, 0.15), transparent 60%),
    radial-gradient(circle at 70% 70%, rgba(99, 102, 241, 0.1), transparent 60%);
}

.icon {
  width: 5rem;
  height: 5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(59, 130, 246, 0.15);
  color: var(--primary-300);
  border-radius: 1.5rem;
  position: relative;
  z-index: 1;
  transition: all 0.4s ease;
}

.feature-card:hover .icon {
  transform: scale(1.1) rotate(5deg);
  background: var(--primary-600);
  color: white;
}

.card-overlay {
  position: absolute;
  inset: 0;
  background: rgba(15, 23, 42, 0.95);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.feature-card:hover .card-overlay {
  opacity: 1;
}

.quick-view-btn {
  padding: 0.75rem 1.5rem;
  background: var(--primary-600);
  color: white;
  border: none;
  border-radius: 0.75rem;
  font-weight: 600;
  font-size: 0.9375rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  transition: all 0.3s ease;
}

.quick-view-btn:hover {
  background: var(--primary-700);
  transform: scale(1.05);
}

.card-content {
  padding: 1.75rem;
}

.card-header {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 1rem;
  margin-bottom: 1rem;
}

.feature-title {
  font-size: 1.375rem;
  font-weight: 700;
  color: var(--neutral-50);
  line-height: 1.3;
}

.year-badge {
  padding: 0.25rem 0.75rem;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.3);
  color: var(--primary-300);
  border-radius: 1rem;
  font-size: 0.8125rem;
  font-weight: 600;
  white-space: nowrap;
}

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.tech-tag {
  padding: 0.375rem 0.75rem;
  background: rgba(148, 163, 184, 0.1);
  border: 1px solid rgba(148, 163, 184, 0.2);
  color: var(--neutral-300);
  border-radius: 0.5rem;
  font-size: 0.8125rem;
  font-weight: 500;
}

.feature-description {
  color: var(--neutral-300);
  line-height: 1.6;
  font-size: 0.9375rem;
  margin-bottom: 1.5rem;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.card-footer {
  padding-top: 1.5rem;
  border-top: 1px solid rgba(148, 163, 184, 0.1);
}

.feature-links {
  display: flex;
  gap: 0.75rem;
}

.link-btn {
  flex: 1;
  padding: 0.75rem 1.25rem;
  border-radius: 0.75rem;
  font-size: 0.875rem;
  font-weight: 600;
  text-decoration: none;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  transition: all 0.3s ease;
}

.link-primary {
  background: var(--primary-600);
  color: white;
}

.link-primary:hover {
  background: var(--primary-700);
  transform: translateY(-2px);
}

.link-secondary {
  background: rgba(148, 163, 184, 0.1);
  color: var(--neutral-200);
  border: 1px solid rgba(148, 163, 184, 0.3);
}

.link-secondary:hover {
  background: rgba(148, 163, 184, 0.15);
  border-color: var(--neutral-400);
  transform: translateY(-2px);
}

.empty-state {
  text-align: center;
  padding: 4rem 2rem;
  color: var(--neutral-400);
}

.empty-state svg {
  margin: 0 auto 1rem;
  opacity: 0.5;
}

.empty-state p {
  font-size: 1.125rem;
}

/* Modal Styles */
.modal-backdrop {
  position: fixed;
  inset: 0;
  background: rgba(15, 23, 42, 0.95);
  backdrop-filter: blur(10px);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  z-index: 1000;
  overflow-y: auto;
}

.modal {
  width: 100%;
  max-width: 800px;
  background: linear-gradient(135deg, rgba(30, 41, 59, 0.95) 0%, rgba(15, 23, 42, 0.98) 100%);
  border: 1px solid rgba(148, 163, 184, 0.2);
  border-radius: 1.5rem;
  padding: 3rem;
  position: relative;
  box-shadow: 0 25px 100px rgba(0, 0, 0, 0.5);
}

.modal-close {
  position: absolute;
  top: 1.5rem;
  right: 1.5rem;
  width: 2.5rem;
  height: 2.5rem;
  border: none;
  background: rgba(148, 163, 184, 0.1);
  color: var(--neutral-400);
  border-radius: 0.75rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
}

.modal-close:hover {
  background: rgba(239, 68, 68, 0.2);
  color: var(--neutral-100);
}

.modal-hero {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.modal-icon {
  width: 5rem;
  height: 5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, var(--primary-600) 0%, var(--primary-700) 100%);
  color: white;
  border-radius: 1.25rem;
  flex-shrink: 0;
}

.modal-title {
  font-size: 2rem;
  font-weight: 800;
  color: var(--neutral-50);
  margin-bottom: 0.5rem;
  line-height: 1.2;
}

.modal-meta {
  font-size: 0.9375rem;
  color: var(--neutral-400);
}

.modal-description {
  color: var(--neutral-200);
  line-height: 1.7;
  font-size: 1.0625rem;
  margin-bottom: 2rem;
}

.modal-details {
  display: grid;
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.detail-card {
  padding: 1.5rem;
  background: rgba(15, 23, 42, 0.6);
  border: 1px solid rgba(148, 163, 184, 0.15);
  border-radius: 1rem;
  display: flex;
  gap: 1rem;
}

.detail-icon {
  width: 2.5rem;
  height: 2.5rem;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(59, 130, 246, 0.15);
  color: var(--primary-400);
  border-radius: 0.75rem;
}

.detail-title {
  font-size: 0.9375rem;
  font-weight: 700;
  color: var(--neutral-100);
  margin-bottom: 0.5rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.detail-text {
  color: var(--neutral-300);
  line-height: 1.6;
  font-size: 0.9375rem;
}

.modal-actions {
  display: flex;
  gap: 1rem;
  padding-top: 2rem;
  border-top: 1px solid rgba(148, 163, 184, 0.1);
}

.modal-btn {
  flex: 1;
  padding: 1rem 2rem;
  border-radius: 0.75rem;
  font-weight: 600;
  font-size: 1rem;
  text-decoration: none;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  transition: all 0.3s ease;
}

.modal-btn-primary {
  background: var(--primary-600);
  color: white;
}

.modal-btn-primary:hover {
  background: var(--primary-700);
  transform: translateY(-2px);
  box-shadow: 0 8px 30px rgba(59, 130, 246, 0.4);
}

.modal-btn-secondary {
  background: rgba(148, 163, 184, 0.1);
  color: var(--neutral-200);
  border: 1.5px solid rgba(148, 163, 184, 0.3);
}

.modal-btn-secondary:hover {
  background: rgba(148, 163, 184, 0.15);
  border-color: var(--neutral-400);
  transform: translateY(-2px);
}

/* Modal Transitions */
.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.3s ease;
}

.modal-enter-active .modal,
.modal-leave-active .modal {
  transition: all 0.3s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}

.modal-enter-from .modal,
.modal-leave-to .modal {
  transform: scale(0.95) translateY(20px);
}

/* Responsive Design */
@media (max-width: 1024px) {
  .features-grid {
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  }
}

@media (max-width: 768px) {
  .projects {
    padding: 4rem 0;
  }

  .container {
    padding: 0 1.5rem;
  }

  .section-title {
    font-size: 2.25rem;
  }

  .filter-tabs {
    width: 100%;
    overflow-x: auto;
    flex-wrap: nowrap;
  }

  .filter-tab {
    white-space: nowrap;
  }

  .features-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .modal {
    padding: 2rem;
    margin: 1rem;
  }

  .modal-hero {
    flex-direction: column;
    align-items: flex-start;
  }

  .modal-title {
    font-size: 1.5rem;
  }

  .modal-actions {
    flex-direction: column;
  }
}

@media (max-width: 480px) {
  .section-header {
    margin-bottom: 2.5rem;
  }

  .modal {
    padding: 1.5rem;
  }

  .card-content {
    padding: 1.25rem;
  }

  .feature-links {
    flex-direction: column;
  }
}
</style>