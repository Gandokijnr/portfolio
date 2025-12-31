<template>
  <section id="projects" class="projects">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">Featured Projects</h2>
        <p class="section-subtitle">
          A selection of web applications I've built recently.
        </p>
      </div>

      <div class="features-grid">
        <div class="feature-card" v-for="feature in features" :key="feature.title">
          <div class="icon" v-html="feature.icon"></div>
          <h3 class="feature-title">{{ feature.title }}</h3>
          <p v-if="feature.meta" class="feature-meta">{{ feature.meta }}</p>
          <p class="feature-description">{{ feature.description }}</p>
          <div
            v-if="feature.problem || feature.who || feature.impact || feature.liveUrl || feature.codeUrl"
            class="feature-links"
          >
            <button
              v-if="feature.problem || feature.who || feature.impact"
              type="button"
              class="feature-link feature-link-button"
              @click="openFeature(feature)"
            >
              View more
            </button>
            <a
              v-if="feature.liveUrl"
              :href="feature.liveUrl"
              class="feature-link"
              target="_blank"
              rel="noopener noreferrer"
            >
              View live
            </a>
            <a
              v-if="feature.codeUrl"
              :href="feature.codeUrl"
              class="feature-link"
              target="_blank"
              rel="noopener noreferrer"
            >
              View code
            </a>
          </div>
        </div>
      </div>
    </div>

    <div v-if="selectedFeature" class="modal-backdrop" @click.self="closeModal">
      <div class="modal">
        <button type="button" class="modal-close" @click="closeModal">
          ×
        </button>
        <div class="modal-header">
          <h3 class="modal-title">{{ selectedFeature.title }}</h3>
          <p v-if="selectedFeature.meta" class="modal-meta">
            {{ selectedFeature.meta }}
          </p>
        </div>
        <p class="modal-description">
          {{ selectedFeature.description }}
        </p>
        <div
          v-if="selectedFeature.problem || selectedFeature.who || selectedFeature.impact"
          class="modal-grid"
        >
          <div v-if="selectedFeature.problem" class="modal-section">
            <h4 class="modal-section-title">Problem</h4>
            <p>{{ selectedFeature.problem }}</p>
          </div>
          <div v-if="selectedFeature.who" class="modal-section">
            <h4 class="modal-section-title">Who</h4>
            <p>{{ selectedFeature.who }}</p>
          </div>
          <div v-if="selectedFeature.impact" class="modal-section">
            <h4 class="modal-section-title">Impact</h4>
            <p>{{ selectedFeature.impact }}</p>
          </div>
        </div>
        <div
          v-if="selectedFeature.liveUrl || selectedFeature.codeUrl"
          class="modal-links"
        >
          <a
            v-if="selectedFeature.liveUrl"
            :href="selectedFeature.liveUrl"
            class="feature-link"
            target="_blank"
            rel="noopener noreferrer"
          >
            View live
          </a>
          <a
            v-if="selectedFeature.codeUrl"
            :href="selectedFeature.codeUrl"
            class="feature-link"
            target="_blank"
            rel="noopener noreferrer"
          >
            View code
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const features = [
  {
    title: 'Selify (Jiji.ng Alternative)',
    meta: 'E-commerce · 2023 · Advanced · 3 months',
    description:
      'Selify is a modern classifieds marketplace where users can quickly list items like phones, cars, electronics, services, and more. Buyers can browse or post what they’re looking for, and sellers can respond directly. The platform offers smart pricing suggestions, verified listings, and a clean interface to make transactions faster and safer.',
    liveUrl: 'https://www.selify.ng',
    codeUrl: 'https://github.com/Gandokijnr',
    problem:
      'Informal, fragmented marketplaces make it hard for everyday buyers and sellers to discover trustworthy listings and complete secure transactions.',
    who:
      'Individual sellers and small merchants in Nigeria looking to buy and sell products safely online.',
    impact:
      "Selify is a modern, user-centric marketplace platform designed to empower buyers and sellers across Nigeria and beyond. Our mission is to make buying and selling simple, safe, and rewarding for everyone, whether you're looking for electronics, vehicles, real estate, services, or more.",
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h7l7 7-7 7-7-7z"/><circle cx="9" cy="7" r="1"/></svg>'
  },
  {
    title: 'VisionGardens Hotels',
    meta: 'Web Apps · 2025',
    description:
      'VisionGardens Hotels is a luxury booking platform that turns outdated hotel websites into a real-time, high-converting reservation experience.',
    problem:
      'Premium hotels often struggle to present their value online and handle bookings smoothly due to clunky websites and lack of real-time availability.',
    who:
      'Boutique and luxury hotel owners who want to attract high-value guests through a modern digital experience.',
    impact:
      'By combining elegant room showcases, real-time availability, and seamless reservations, VisionGardens Hotels increases direct bookings and strengthens brand perception.',
    liveUrl: 'https://visiongardenshotel.com/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 10h18v8H3z"/><path d="M7 10V7a3 3 0 0 1 3-3h4a3 3 0 0 1 3 3v3"/></svg>'
  },
  {
    title: 'Roomio',
    meta: 'SaaS · 2025 · Advanced · 2 months',
    description:
      'Transform your hotel operations with Roomio: effortless bookings, automated housekeeping, profit-driven revenue tools, connected operations, and actionable analytics all in one platform trusted by hotels to cut operational costs by 40%.',
    problem:
      'Hotels often struggle with fragmented systems — one tool for bookings, another for housekeeping, another for payments, and spreadsheets for analytics. This leads to errors, delays, staff stress, lost revenue opportunities, and an inconsistent guest experience.',
    who:
      'Roomio is built for hotels, boutique stays, resorts, and serviced apartments looking to streamline operations, improve efficiency, reduce manual work, and scale without hiring more staff or increasing complexity.',
    impact:
      'Roomio centralizes availability, payments, and reservation management so operators reduce admin overhead and deliver a smoother guest journey.',
    liveUrl: 'https://roommio.netlify.app/landing',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="4" y="4" width="9" height="14" rx="1"/><path d="M7 7h3M7 11h3M7 15h3"/><circle cx="18" cy="13" r="3"/><path d="M18 10.5v1"/><path d="M18 14.5v1"/><path d="M20.5 13H19"/><path d="M17 13h-1.5"/></svg>'
  },
  {
    title: 'Winebay',
    meta: 'E-commerce · 2025 · Advanced · 2 months',
    description:
      'Winebay is a modern e-commerce experience for discovering and purchasing curated wines, combining rich product storytelling with a smooth checkout flow.',
    problem:
      'Wine lovers and boutique wine brands struggle with fragmented online shopping experiences that lack discovery tools, education, and trust-building content.',
    who:
      'Wine enthusiasts, collectors, and boutique wine brands looking for a better way to discover, showcase, and purchase curated bottles online.',
    impact:
      'Winebay makes it easier to discover the right bottle, compare options, and purchase with confidence through a polished, conversion-focused shopping experience.',
    liveUrl: 'https://winebay.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M9 3h2v5a2 2 0 0 1-2 2v7"/><path d="M15 3h2v5a3 3 0 0 1-3 3h0a3 3 0 0 1-3-3V3h2"/><path d="M13 20h4"/></svg>'
  },
  {
    title: 'My UniCamp',
    meta: 'Web Apps · 2025',
    description:
      'My UniCamp is a course discovery platform that turns scattered university information into a clear, searchable catalog of programs worldwide.',
    problem:
      'Prospective students are overwhelmed by scattered university information and struggle to compare programs across schools.',
    who:
      'High school graduates, career switchers, and lifelong learners researching degree or certificate programs.',
    impact:
      'My UniCamp simplifies program discovery, helping users quickly find relevant courses and make more confident education decisions.',
    liveUrl: 'https://myunicamp.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 7l9-4 9 4-9 4-9-4z"/><path d="M7 10v5a5 5 0 0 0 10 0v-5"/><path d="M12 11v8"/></svg>'
  },
  {
    title: 'Farmxic',
    meta: 'Web Apps · 2024 · Advanced · 3 months',
    description:
      'Farmxic is an agricultural platform that turns isolated farming efforts into a connected ecosystem of modern tools, knowledge, and market opportunities.',
    problem:
      'Small and mid-scale farmers often lack access to modern techniques, reliable markets, and relevant agricultural information.',
    who:
      'Farmers and agricultural cooperatives seeking better tools, knowledge, and market connections.',
    impact:
      'Farmxic connects farmers to resources and market access, helping them improve yields, income, and resilience.',
    liveUrl: 'https://www.farmxic.com/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 20c4-6 8-8 16-8-2.5 3-6 5-10 6.5"/><path d="M10 20c0-6 2-10 6-13"/></svg>'
  },
  {
    title: 'SurePicks',
    meta: 'Web Apps · 2025 · Advanced · 2 months',
    description:
      'SurePicks is a sports prediction platform that replaces gut-feel betting with data-driven insights and real-time odds.',
    problem:
      'Sports bettors often rely on guesswork or low-quality tips, resulting in uninformed bets and inconsistent outcomes.',
    who:
      'Recreational and semi-professional sports bettors seeking a data-backed edge.',
    impact:
      'SurePicks uses analytics, odds, and expert insights to help users make more informed betting decisions and manage risk more intelligently.',
    liveUrl: 'https://surepicks.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 19V9"/><path d="M9 19V5"/><path d="M14 19v-7"/><path d="M17 8l2 2 3-3"/></svg>'
  },
  {
    title: 'Real Estate Web Page',
    meta: 'Landing Pages · 2024 · Intermediate · 2 months',
    description:
      'The Real Estate Web Page is a modern listings interface that turns static property catalogs into a responsive, searchable home-hunting experience.',
    problem:
      'Homebuyers and investors struggle to find relevant properties when real estate listings are poorly presented or hard to search.',
    who:
      'Real estate agencies and property developers needing a modern online presence for their listings.',
    impact:
      'This real estate web page makes properties easier to browse and filter, driving more qualified leads and higher engagement.',
    liveUrl: 'https://gidiestate.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 11l9-7 9 7v9a1 1 0 0 1-1 1h-5v-6H9v6H4a1 1 0 0 1-1-1z"/></svg>'
  },
  {
    title: 'Agency Aggregator App',
    meta: 'Web Apps · 2025 · Advanced · 3 months',
    description:
      'Agency Aggregator is a management platform that replaces scattered agency spreadsheets with a secure, all-in-one dashboard for teams, clients, and data.',
    problem:
      'Agencies often manage clients, projects, and teams across spreadsheets and disconnected tools, creating data silos and operational blind spots.',
    who:
      'Agency owners and operations managers at digital, creative, or marketing agencies.',
    impact:
      'Agency Aggregator centralizes data with role-based access and dashboards, improving control, visibility, and day-to-day efficiency.',
    liveUrl: 'https://agencyaggregator.netlify.app/auth/login',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16v4H4zM4 10h10v4H4zM4 16h7v4H4z"/></svg>'
  },
  {
    title: 'Fx Trading Learning Web App',
    meta: 'Web Apps · 2024 · Advanced · 3 months',
    description:
      'The Fx Trading Learning Web App is an educational platform that turns scattered forex knowledge into structured, actionable learning.',
    problem:
      'Aspiring forex traders face steep learning curves and fragmented educational resources, leading to costly mistakes in live markets.',
    who:
      'Beginner and intermediate forex traders who want structured, practical learning.',
    impact:
      'The app provides guided modules, analysis tools, and trading guides that reduce confusion and help users make more informed trading decisions.',
    liveUrl: 'https://gandokigroup.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 20V10m4 10V6m4 14V8m4 12V4"/></svg>'
  },
  {
    title: 'Job Navigator',
    meta: 'Web Apps · 2023 · Intermediate · 2 months',
    description:
      'Job Navigator is a job search platform that transforms scattered applications into a single, trackable job-hunting workspace.',
    problem:
      'Job seekers waste time jumping between platforms and struggle to track applications or find roles that truly match their profiles.',
    who:
      'Early- and mid-career professionals actively searching for new opportunities.',
    impact:
      'Job Navigator consolidates listings, filters, and application tracking so users can run a more focused, organized job search.',
    liveUrl: 'https://jobnavigator.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16v4H4zM4 10h12v4H4zM4 16h8v4H4z"/></svg>'
  },
  {
    title: 'Trade Ventures E-commerce',
    meta: 'E-commerce · 2023 · Advanced · 4 months',
    description:
      'Trade Ventures E-commerce is a full-featured online store that replaces basic catalogs with carts, payments, inventory control, and admin dashboards.',
    problem:
      'Product-based businesses struggle to sell online when they lack a robust storefront with inventory, payments, and admin tooling.',
    who:
      'Small and medium retailers looking to launch or upgrade their online sales channel.',
    impact:
      'Trade Ventures E-commerce provides a complete buying experience and back-office tools, increasing sales while simplifying operations.',
    liveUrl: 'https://tradeventures.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M6 6h15l-1.5 9h-12z"/><circle cx="9" cy="19" r="1.5"/><circle cx="18" cy="19" r="1.5"/><path d="M3 3h2l1 3"/></svg>'
  },
  {
    title: 'Calculator Web App',
    meta: 'Web Apps · 2023 · Beginner · 3 days',
    description:
      'The Calculator Web App is a modern browser-based calculator that turns one-off calculations into a fast, traceable workflow.',
    problem:
      'Users needing quick calculations often rely on basic tools that lack advanced functions or history, making it easy to repeat work or make errors.',
    who:
      'Students, analysts, and professionals doing frequent ad-hoc calculations in the browser.',
    impact:
      'The calculator’s advanced functions and history tracking speed up calculations and reduce mistakes.',
    liveUrl: 'https://caluculatingapp.netlify.app/',
    codeUrl: 'https://github.com/Gandokijnr',
    icon: '<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="4" y="3" width="16" height="18" rx="2"/><path d="M8 8h8M8 12h2m4 0h2M8 16h2m4 0h2"/></svg>'
  }
];

const selectedFeature = ref(null);

const openFeature = (feature) => {
  selectedFeature.value = feature;
};

const closeModal = () => {
  selectedFeature.value = null;
};
</script>

<style scoped>
.projects {
	position: relative;
	padding: var(--spacing-3xl) 0;
	background:
		radial-gradient(circle at -10% 0%, rgba(255, 106, 61, 0.18), transparent 55%),
		radial-gradient(circle at 110% 100%, rgba(138, 30, 255, 0.4), transparent 55%),
		linear-gradient(180deg, var(--neutral-900) 0%, var(--neutral-950) 100%);
	overflow: hidden;
}

.container {
	max-width: 1400px;
	margin: 0 auto;
	padding: 0 var(--spacing-lg);
}

.section-header {
	text-align: left;
	margin-bottom: var(--spacing-3xl);
	max-width: 640px;
}

.section-title {
  font-size: 2.5rem;
  color: var(--neutral-50);
  margin-bottom: var(--spacing-sm);
}

.section-subtitle {
  font-size: 1.125rem;
  color: var(--neutral-300);
  max-width: 600px;
  margin: 0 auto;
}

.features-grid {
	display: flex;
	gap: var(--spacing-xl);
	overflow-x: auto;
	overflow-y: visible;
	padding-bottom: calc(var(--spacing-lg) + 0.5rem);
	scroll-snap-type: x mandatory;
	scroll-padding-left: var(--spacing-lg);
	-webkit-overflow-scrolling: touch;
}

.feature-card {
	position: relative;
	flex: 0 0 auto;
	min-width: min(80vw, 520px);
	padding: var(--spacing-xl);
	background:
		linear-gradient(145deg, rgba(5, 0, 10, 0.95), rgba(36, 28, 56, 0.98)),
		radial-gradient(circle at 0% 0%, rgba(255, 239, 234, 0.267), transparent 55%);
	border-radius: 1.75rem;
	transition: transform 0.4s ease, box-shadow 0.4s ease, border-color 0.3s ease;
	border: 1px solid rgba(168, 154, 196, 0.6);
	scroll-snap-align: start;
}

.feature-card:hover {
	transform: translateY(-10px) rotate3d(1, -1, 0, 6deg) scale(1.01);
	border-color: var(--primary-500);
	box-shadow: 0 28px 80px rgba(0, 0, 0, 0.95);
}

.icon {
  width: 3rem;
  height: 3rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(37, 99, 235, 0.15);
  color: var(--primary-100);
  border-radius: 0.75rem;
  margin-bottom: var(--spacing-md);
  transition: all 0.3s ease;
}

.feature-card:hover .icon {
  background: var(--primary-600);
  color: white;
  transform: scale(1.1);
}

.feature-title {
  font-size: 1.25rem;
  color: var(--neutral-50);
  margin-bottom: var(--spacing-sm);
}

.feature-meta {
  font-size: 0.875rem;
  color: var(--neutral-400);
  margin-bottom: var(--spacing-xs);
}

.feature-description {
  color: var(--neutral-300);
  line-height: 1.5;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.feature-links {
  margin-top: var(--spacing-md);
  display: flex;
  gap: var(--spacing-sm);
  flex-wrap: wrap;
}

.feature-link {
  font-size: 0.875rem;
  color: var(--primary-300);
  text-decoration: none;
  font-weight: 500;
}

.feature-link:hover {
  color: var(--primary-100);
  text-decoration: underline;
}

.feature-link-button {
  border-radius: 999px;
  border: 1px solid rgba(148, 163, 184, 0.5);
  padding: 0.35rem 0.9rem;
  background: rgba(15, 23, 42, 0.9);
}

.feature-link-button:hover {
  background: rgba(15, 23, 42, 1);
  border-color: var(--primary-500);
}

.modal-backdrop {
  position: fixed;
  inset: 0;
  background: rgba(15, 23, 42, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: var(--spacing-md);
  z-index: 50;
}

.modal {
  width: 100%;
  max-width: 640px;
  background: rgba(15, 23, 42, 1);
  border-radius: 1rem;
  border: 1px solid rgba(148, 163, 184, 0.6);
  box-shadow: 0 24px 80px rgba(15, 23, 42, 0.9);
  padding: var(--spacing-xl);
  position: relative;
  max-height: calc(100vh - 2 * var(--spacing-md));
  overflow-y: auto;
}

.modal-header {
  margin-bottom: var(--spacing-sm);
}

.modal-title {
  font-size: 1.5rem;
  color: var(--neutral-50);
  margin-bottom: 0.25rem;
}

.modal-meta {
  font-size: 0.875rem;
  color: var(--neutral-400);
}

.modal-description {
  margin-top: var(--spacing-md);
  margin-bottom: var(--spacing-md);
  color: var(--neutral-200);
}

.modal-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: var(--spacing-md);
  margin-top: var(--spacing-md);
}

.modal-section-title {
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--neutral-100);
  margin-bottom: 0.25rem;
}

.modal-section p {
  font-size: 0.9rem;
  color: var(--neutral-300);
}

.modal-links {
  margin-top: var(--spacing-lg);
  display: flex;
  gap: var(--spacing-sm);
  flex-wrap: wrap;
}

.modal-close {
  position: absolute;
  top: 1rem;
  right: 1rem;
  border: none;
  background: transparent;
  color: var(--neutral-400);
  font-size: 1.5rem;
  line-height: 1;
  cursor: pointer;
}

.modal-close:hover {
  color: var(--neutral-100);
}

@media (max-width: 640px) {
  .features-grid {
    grid-template-columns: 1fr;
  }

  .section-title {
    font-size: 2rem;
  }

  .projects {
    padding: var(--spacing-2xl) 0;
  }

  .feature-card {
    padding: var(--spacing-lg);
  }

  .modal {
    padding: var(--spacing-lg);
  }
}

@media (max-width: 480px) {
  .modal {
    padding: var(--spacing-md);
  }
}
</style>
