<template>
  <header class="main-header">
    <nav class="navbar">
      <a href="#about" class="logo" @click="navigate('#about')">⚡ Fares Ben Ali</a>

      <button
        class="menu-toggle"
        type="button"
        :aria-expanded="menuOpen ? 'true' : 'false'"
        aria-label="Toggle navigation menu"
        @click="menuOpen = !menuOpen"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>

      <ul class="nav-links" :class="{ open: menuOpen }">
        <li><a :class="{ active: currentSection === '#about' }" href="#about" @click.prevent="navigate('#about')">👤 About</a></li>
        <li><a :class="{ active: currentSection === '#skills' }" href="#skills" @click.prevent="navigate('#skills')">🧠 Skills</a></li>
        <li><a :class="{ active: currentSection === '#experience' }" href="#experience" @click.prevent="navigate('#experience')">💼 Experience</a></li>
        <li><a :class="{ active: currentSection === '#projects' }" href="#projects" @click.prevent="navigate('#projects')">📂 Projects</a></li>
        <li><a :class="{ active: currentSection === '#contact' }" href="#contact" @click.prevent="navigate('#contact')">📬 Contact</a></li>
      </ul>
    </nav>


  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      menuOpen: false,
      currentSection: window.location.hash || '#about'
    };
  },
  computed: {
    sectionLabel() {
      const labels = {
        '#about': 'ABOUT',
        '#skills': 'SKILLS',
        '#experience': 'EXPERIENCE',
        '#projects': 'PROJECTS',
        '#contact': 'CONTACT'
      };
      return labels[this.currentSection] || 'HOME';
    }
  },
  methods: {
    closeMenu() {
      this.menuOpen = false;
    },
    updateSection() {
      this.currentSection = window.location.hash || '#about';
    },
    navigate(hash) {
      this.menuOpen = false;
      this.currentSection = hash;
      window.location.hash = hash;
      setTimeout(() => window.scrollTo({ top: document.querySelector(hash)?.offsetTop - 70 || 0, behavior: 'smooth' }), 50);
    }
  },
  mounted() {
    window.addEventListener('hashchange', this.updateSection);
    this.updateSection();
  },
  beforeUnmount() {
    window.removeEventListener('hashchange', this.updateSection);
  }
};
</script>

<style scoped>
.main-header {
  position: sticky;
  top: 0;
  z-index: 1000;
  background: linear-gradient(135deg, rgba(5, 13, 28, 0.92), rgba(16, 23, 44, 0.72));
  backdrop-filter: blur(18px);
  border-bottom: 1px solid rgba(0, 229, 255, 0.3);
  box-shadow: 0 0 28px rgba(0, 229, 255, 0.24);
  border-radius: 0 0 16px 16px;
  padding-top: 0.25rem;
}

.navbar {
  max-width: 1200px;
  margin: 0 auto;
  min-height: 72px;
  padding: 0.6rem 1rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  position: relative;
}

.logo {
  color: var(--orange);
  text-decoration: none;
  font-weight: 700;
  letter-spacing: 0.3px;
  white-space: nowrap;
}

.menu-toggle {
  display: none;
  width: 42px;
  height: 42px;
  border-radius: 10px;
  border: 1px solid var(--line);
  background: transparent;
  cursor: pointer;
  padding: 8px;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 5px;
}

.menu-toggle span {
  width: 18px;
  height: 2px;
  background: var(--white);
  display: block;
}

.nav-links {
  list-style: none;
  display: flex;
  gap: 1.25rem;
  margin: 0;
  padding: 0;
}

.nav-links a {
  color: var(--white);
  text-decoration: none;
  font-size: 0.95rem;
  transition: color 0.25s ease;
}

.nav-links a:hover,
.nav-links a.active {
  color: #00e5ff;
  text-shadow: 0 0 12px rgba(0, 229, 255, 0.75), 0 0 24px rgba(0, 229, 255, 0.5);
}

.nav-links a.active {
  box-shadow: inset 0 -2px 0 0 #00e5ff, 0 0 10px rgba(0, 229, 255, 0.35);
  border-radius: 6px;
  background: rgba(0, 229, 255, 0.1);
}

.tracker {
  max-width: 1200px;
  margin: 0.35rem auto 0;
  padding: 0.45rem 1rem;
  color: #baf8ff;
  font-size: 0.84rem;
  letter-spacing: 1px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  background: linear-gradient(to right, rgba(0, 229, 255, 0.12), rgba(22, 10, 52, 0.2));
  border: 1px solid rgba(0, 229, 255, 0.25);
  border-radius: 999px;
  box-shadow: 0 0 32px rgba(0, 229, 255, 0.18);
}

.tracker strong {
  color: #ffffff;
  font-weight: 900;
  text-shadow: 0 0 10px rgba(0, 229, 255, 0.7);
}

.tracker .pulse {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #00e5ff;
  box-shadow: 0 0 8px rgba(0, 229, 255, 0.9), 0 0 20px rgba(0, 229, 255, 0.45);
  animation: pulse 1.35s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% { transform: scale(1); opacity: 1; }
  50% { transform: scale(1.5); opacity: 0.4; }
}

@media (max-width: 900px) {
  .menu-toggle {
    display: inline-flex;
  }

  .nav-links {
    position: absolute;
    top: calc(100% + 8px);
    right: 1rem;
    left: 1rem;
    display: grid;
    gap: 0.35rem;
    background: color-mix(in srgb, var(--panel-strong) 92%, transparent);
    border: 1px solid var(--line);
    border-radius: 12px;
    padding: 0.6rem;
    box-shadow: 0 12px 30px rgba(0, 0, 0, 0.28);
    transform: translateY(-6px);
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.2s ease, transform 0.2s ease;
  }

  .nav-links.open {
    transform: translateY(0);
    opacity: 1;
    pointer-events: auto;
  }

  .nav-links a {
    display: block;
    width: 100%;
    padding: 0.7rem 0.75rem;
    border-radius: 8px;
  }

  .nav-links a:hover {
    background: color-mix(in srgb, var(--orange) 18%, var(--prussian-blue));
  }
}
</style>