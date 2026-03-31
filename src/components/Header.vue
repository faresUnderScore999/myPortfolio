<template>
  <header class="main-header">
    <div class="header-glow"></div>
    <nav class="navbar">
      <a href="#about" class="logo" @click="navigate('#about')">
        <span class="logo-icon">⚡</span>
        <span class="logo-text">Fares Ben Ali</span>
        <span class="logo-glow"></span>
      </a>
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
        <li v-for="(link, index) in navLinks" :key="link.hash" :class="`nav-item-${index}`">
          <a
            :class="{ active: currentSection === link.hash }"
            :href="link.hash"
            @click.prevent="navigate(link.hash)"
          >
            <span class="nav-icon">{{ link.icon }}</span>
            <span class="nav-text">{{ link.label }}</span>
            <span class="nav-glow"></span>
          </a>
        </li>
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
      currentSection: window.location.hash || '#about',
      navLinks: [
        { hash: '#about', label: 'About', icon: '👤' },
        { hash: '#education', label: 'Education', icon: '🎓' },
        { hash: '#skills', label: 'Skills', icon: '🧠' },
        { hash: '#projects', label: 'Projects', icon: '📂' },
        { hash: '#github', label: 'GitHub', icon: '🐙' },
        { hash: '#experience', label: 'Experience', icon: '💼' },
        { hash: '#contact', label: 'Contact', icon: '📬' }
      ]
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
  background: linear-gradient(135deg, rgba(5, 13, 28, 0.98), rgba(16, 23, 44, 0.9));
  backdrop-filter: blur(25px);
  -webkit-backdrop-filter: blur(25px);
  border-bottom: 1px solid var(--line);
  box-shadow: 
    0 4px 30px rgba(0, 0, 0, 0.4),
    0 0 40px rgba(252, 163, 17, 0.1),
    inset 0 -1px 0 rgba(252, 163, 17, 0.1);
  border-radius: 0 0 24px 24px;
  padding-top: 0.25rem;
  overflow: hidden;
}

.header-glow {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(90deg, 
    transparent, 
    var(--orange), 
    rgba(252, 163, 17, 0.5),
    var(--orange), 
    transparent
  );
  animation: headerGlow 3s ease-in-out infinite;
}

@keyframes headerGlow {
  0%, 100% { opacity: 0.5; }
  50% { opacity: 1; }
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
  font-size: 1.2rem;
  transition: var(--transition-medium);
  position: relative;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  border-radius: 12px;
  background: rgba(252, 163, 17, 0.05);
  border: 1px solid transparent;
}

.logo:hover {
  background: rgba(252, 163, 17, 0.15);
  border-color: var(--orange);
  transform: scale(1.02);
}

.logo-icon {
  font-size: 1.4rem;
  animation: pulse 2s ease-in-out infinite;
}

.logo-text {
  position: relative;
  z-index: 1;
}

.logo-glow {
  position: absolute;
  inset: 0;
  border-radius: 12px;
  background: radial-gradient(circle at center, rgba(252, 163, 17, 0.3), transparent 70%);
  opacity: 0;
  transition: var(--transition-medium);
}

.logo:hover .logo-glow {
  opacity: 1;
  animation: glow 2s ease-in-out infinite;
}

.menu-toggle {
  display: none;
  width: 48px;
  height: 48px;
  border-radius: 14px;
  border: 1px solid var(--line);
  background: rgba(252, 163, 17, 0.08);
  cursor: pointer;
  padding: 12px;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 5px;
  transition: var(--transition-fast);
  position: relative;
}

.menu-toggle:hover {
  background: rgba(252, 163, 17, 0.2);
  border-color: var(--orange);
  box-shadow: 0 0 20px rgba(252, 163, 17, 0.3);
}

.menu-toggle span {
  width: 22px;
  height: 2px;
  background: var(--white);
  display: block;
  border-radius: 2px;
  transition: var(--transition-fast);
  position: relative;
}

.menu-toggle[aria-expanded='true'] span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.menu-toggle[aria-expanded='true'] span:nth-child(2) {
  opacity: 0;
  transform: translateX(-10px);
}

.menu-toggle[aria-expanded='true'] span:nth-child(3) {
  transform: rotate(-45deg) translate(5px, -5px);
}

.nav-links {
  list-style: none;
  display: flex;
  gap: 0.25rem;
  margin: 0;
  padding: 0;
}

.nav-links a {
  color: var(--text-soft);
  text-decoration: none;
  font-size: 0.85rem;
  font-weight: 500;
  padding: 0.5rem 0.75rem;
  border-radius: 10px;
  transition: var(--transition-fast);
  position: relative;
  display: flex;
  align-items: center;
  gap: 0.4rem;
  overflow: hidden;
}

.nav-icon {
  font-size: 1rem;
  transition: var(--transition-fast);
}

.nav-text {
  position: relative;
  z-index: 1;
}

.nav-glow {
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at center, rgba(252, 163, 17, 0.2), transparent 70%);
  opacity: 0;
  transition: var(--transition-medium);
}

.nav-links a::before {
  content: '';
  position: absolute;
  bottom: 0;
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
  transform: translateY(-2px);
}

.nav-links a:hover .nav-icon,
.nav-links a.active .nav-icon {
  transform: scale(1.2);
}

.nav-links a:hover::before,
.nav-links a.active::before {
  width: 60%;
}

.nav-links a:hover .nav-glow,
.nav-links a.active .nav-glow {
  opacity: 1;
}

.nav-links a.active {
  box-shadow: 0 0 20px rgba(252, 163, 17, 0.3);
}

/* Staggered animation for nav items */
.nav-item-0 { animation: slideInLeft 0.5s ease backwards; }
.nav-item-1 { animation: slideInLeft 0.5s ease 0.05s backwards; }
.nav-item-2 { animation: slideInLeft 0.5s ease 0.1s backwards; }
.nav-item-3 { animation: slideInLeft 0.5s ease 0.15s backwards; }
.nav-item-4 { animation: slideInLeft 0.5s ease 0.2s backwards; }
.nav-item-5 { animation: slideInLeft 0.5s ease 0.25s backwards; }
.nav-item-6 { animation: slideInLeft 0.5s ease 0.3s backwards; }

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
    gap: 0.4rem;
    background: linear-gradient(180deg, rgba(20, 33, 61, 0.99), rgba(11, 19, 40, 0.99));
    border: 1px solid var(--line);
    border-radius: 20px;
    padding: 1rem;
    box-shadow: 
      0 25px 60px rgba(0, 0, 0, 0.5), 
      0 0 40px rgba(252, 163, 17, 0.1),
      inset 0 1px 0 rgba(252, 163, 17, 0.1);
    transform: translateY(-15px);
    opacity: 0;
    pointer-events: none;
    transition: opacity 0.3s ease, transform 0.3s ease;
  }

  .nav-links.open {
    transform: translateY(0);
    opacity: 1;
    pointer-events: auto;
  }

  .nav-links a {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    width: 100%;
    padding: 0.9rem 1.1rem;
    border-radius: 12px;
    font-size: 1rem;
  }

  .nav-links a:hover,
  .nav-links a.active {
    background: rgba(252, 163, 17, 0.2);
    transform: translateX(5px);
  }
}
</style>