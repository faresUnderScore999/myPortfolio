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
        <li><a :class="{ active: currentSection === '#education' }" href="#education" @click.prevent="navigate('#education')">🎓 Education</a></li>
        <li><a :class="{ active: currentSection === '#skills' }" href="#skills" @click.prevent="navigate('#skills')">🧠 Skills</a></li>
        <li><a :class="{ active: currentSection === '#projects' }" href="#projects" @click.prevent="navigate('#projects')">📂 Projects</a></li>
        <li><a :class="{ active: currentSection === '#github' }" href="#github" @click.prevent="navigate('#github')">🐙 GitHub</a></li>
        <li><a :class="{ active: currentSection === '#experience' }" href="#experience" @click.prevent="navigate('#experience')">💼 Experience</a></li>
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
    }
  },
  computed: {
    sectionLabel() {
      const labels = {
        '#about': 'ABOUT',
        '#education': 'EDUCATION',
        '#github': 'GITHUB',
        '#skills': 'SKILLS',
        '#experience': 'EXPERIENCE',
        '#projects': 'PROJECTS',
        '#contact': 'CONTACT'
      }
      return labels[this.currentSection] || 'HOME'
    }
  },
  methods: {
    closeMenu() {
      this.menuOpen = false
    },
    updateSection() {
      this.currentSection = window.location.hash || '#about'
    },
    navigate(hash) {
      this.menuOpen = false
      this.currentSection = hash
      window.location.hash = hash
      setTimeout(
        () =>
          window.scrollTo({
            top: document.querySelector(hash)?.offsetTop - 70 || 0,
            behavior: 'smooth'
          }),
        50
      )
    }
  },
  mounted() {
    window.addEventListener('hashchange', this.updateSection)
    this.updateSection()
  },
  beforeUnmount() {
    window.removeEventListener('hashchange', this.updateSection)
  }
}
</script>

<style scoped>
.main-header {
  position: sticky;
  top: 0;
  z-index: 1000;
  background: linear-gradient(135deg, rgba(5, 13, 28, 0.95), rgba(16, 23, 44, 0.8));
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--line);
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.3), var(--glow);
  border-radius: 0 0 20px 20px;
  padding-top: 0.25rem;
}

.navbar {
  max-width: 1200px;
  margin: 0 auto;
  min-height: 72px;
  padding: 0.6rem 1.5rem;
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
  font-size: 1.15rem;
  transition: var(--transition-medium);
  position: relative;
}

.logo::before {
  content: '';
  position: absolute;
  left: -12px;
  top: 50%;
  transform: translateY(-50%);
  width: 6px;
  height: 6px;
  background: var(--orange);
  border-radius: 50%;
  box-shadow: var(--glow);
  animation: pulse 2s ease-in-out infinite;
}

.logo:hover {
  text-shadow: var(--glow-strong);
  transform: scale(1.02);
}

.menu-toggle {
  display: none;
  width: 44px;
  height: 44px;
  border-radius: 12px;
  border: 1px solid var(--line);
  background: rgba(252, 163, 17, 0.05);
  cursor: pointer;
  padding: 10px;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 5px;
  transition: var(--transition-fast);
}

.menu-toggle:hover {
  background: rgba(252, 163, 17, 0.15);
  border-color: var(--orange);
}

.menu-toggle span {
  width: 20px;
  height: 2px;
  background: var(--white);
  display: block;
  border-radius: 2px;
  transition: var(--transition-fast);
}

.menu-toggle[aria-expanded='true'] span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.menu-toggle[aria-expanded='true'] span:nth-child(2) {
  opacity: 0;
}

.menu-toggle[aria-expanded='true'] span:nth-child(3) {
  transform: rotate(-45deg) translate(5px, -5px);
}

.nav-links {
  list-style: none;
  display: flex;
  gap: 0.3rem;
  margin: 0;
  padding: 0;
}

.nav-links a {
  color: var(--text-soft);
  text-decoration: none;
  font-size: 0.85rem;
  font-weight: 500;
  padding: 0.45rem 0.7rem;
  border-radius: 8px;
  transition: var(--transition-fast);
  position: relative;
}

.nav-links a::after {
  content: '';
  position: absolute;
  bottom: 4px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 2px;
  background: var(--orange);
  border-radius: 2px;
  transition: var(--transition-fast);
}

.nav-links a:hover,
.nav-links a.active {
  color: var(--orange);
  background: rgba(252, 163, 17, 0.1);
}

.nav-links a:hover::after,
.nav-links a.active::after {
  width: 60%;
}

.nav-links a.active {
  box-shadow: 0 0 15px rgba(252, 163, 17, 0.2);
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
    background: linear-gradient(180deg, rgba(20, 33, 61, 0.98), rgba(11, 19, 40, 0.98));
    border: 1px solid var(--line);
    border-radius: 16px;
    padding: 0.8rem;
    box-shadow: 0 20px 50px rgba(0, 0, 0, 0.4), var(--glow);
    transform: translateY(-10px);
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.25s ease, transform 0.25s ease;
  }

  .nav-links.open {
    transform: translateY(0);
    opacity: 1;
    pointer-events: auto;
  }

  .nav-links a {
    display: block;
    width: 100%;
    padding: 0.85rem 1rem;
    border-radius: 10px;
    font-size: 1rem;
  }

  .nav-links a:hover,
  .nav-links a.active {
    background: rgba(252, 163, 17, 0.15);
  }
}
</style>