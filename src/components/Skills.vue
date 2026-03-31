<template>
  <section id="skills" class="skills">
    <div class="section-glow"></div>
    <h2>
      <span class="section-icon">🧩</span>
      <span class="section-title">Skills</span>
    </h2>
    <div class="skills-grid">
      <article 
        v-for="(category, index) in skillCategories" 
        :key="category.title" 
        class="skill-category"
        :class="`skill-${index}`"
      >
        <div class="category-glow"></div>
        <div class="category-icon-wrapper">
          <span class="category-icon">{{ category.icon }}</span>
        </div>
        <h3>{{ category.title }}</h3>
        <ul>
          <li v-for="(skill, skillIndex) in category.skills" :key="skill" :style="{ '--delay': skillIndex * 0.05 + 's' }">
            <span class="skill-bullet">▹</span>
            <span class="skill-name">{{ skill }}</span>
            <span class="skill-sparkle">✦</span>
          </li>
        </ul>
      </article>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      skillCategories: [
        {
          title: 'Frontend',
          icon: '🎨',
          skills: ['Vue.js / Nuxt.js', 'React.js', 'JavaScript (ES6+)', 'HTML5 / CSS3', 'TypeScript']
        },
        {
          title: 'Backend',
          icon: '⚙️',
          skills: ['Node.js / Express', 'Go (Gin Framework)', 'Spring Boot', 'JEE / Java', 'Symfony 6.4', 'REST APIs / GraphQL']
        },
        {
          title: 'Tools & DevOps',
          icon: '🧰',
          skills: ['Docker', 'Git / GitHub', 'Postman API', 'Selenium WebDriver', 'SQL / MongoDB']
        },
        {
          title: 'Other Skills',
          icon: '🔒',
          skills: ['WebRTC', 'Cybersecurity', 'Méthodes Agiles', 'Routeurs Cisco', 'Python']
        }
      ]
    }
  }
}
</script>

<style scoped>
.skills {
  background: color-mix(in srgb, var(--panel) 90%, transparent);
  border-radius: 24px;
  padding: 3rem 2rem;
  box-shadow: var(--glow), 0 15px 50px rgba(0, 0, 0, 0.35);
  position: relative;
  overflow: hidden;
}

.section-glow {
  position: absolute;
  top: -100px;
  right: -100px;
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(252, 163, 17, 0.12), transparent 70%);
  pointer-events: none;
}

h2 {
  margin-top: 0;
  text-align: center;
  color: var(--white);
  font-size: 2rem;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  position: relative;
  z-index: 1;
}

.section-icon {
  font-size: 2.5rem;
  animation: float 4s ease-in-out infinite;
}

.section-title {
  background: linear-gradient(135deg, var(--white), var(--orange));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
  position: relative;
  z-index: 1;
}

.skill-category {
  border: 1px solid var(--line);
  border-radius: 20px;
  padding: 1.75rem;
  transition: var(--transition-medium);
  background: linear-gradient(180deg, rgba(20, 33, 61, 0.5), rgba(11, 19, 40, 0.8));
  position: relative;
  overflow: hidden;
}

.category-glow {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--orange), #ff6b35, var(--orange));
  background-size: 200% 100%;
  opacity: 0;
  transition: var(--transition-medium);
}

.skill-category:hover .category-glow {
  opacity: 1;
  animation: gradientShift 2s ease infinite;
}

.category-icon-wrapper {
  width: 60px;
  height: 60px;
  background: rgba(252, 163, 17, 0.1);
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1rem;
  position: relative;
  overflow: hidden;
}

.category-icon-wrapper::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at center, rgba(252, 163, 17, 0.3), transparent 70%);
  opacity: 0;
  transition: var(--transition-medium);
}

.skill-category:hover .category-icon-wrapper::before {
  opacity: 1;
}

.category-icon {
  font-size: 1.75rem;
  transition: var(--transition-medium);
}

.skill-category:hover .category-icon {
  transform: scale(1.15) rotate(5deg);
}

h3 {
  margin: 0 0 1.25rem;
  color: var(--orange);
  font-size: 1.15rem;
  font-weight: 600;
}

li {
  color: var(--text-soft);
  margin-bottom: 0.6rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  position: relative;
  padding: 0.4rem 0.6rem;
  border-radius: 8px;
  transition: var(--transition-fast);
  animation: fadeInUp 0.5s ease backwards;
  animation-delay: var(--delay);
}

li:hover {
  background: rgba(252, 163, 17, 0.08);
  transform: translateX(5px);
}

.skill-bullet {
  color: var(--orange);
  font-size: 0.9rem;
  transition: var(--transition-fast);
}

li:hover .skill-bullet {
  transform: scale(1.3);
}

.skill-name {
  flex: 1;
}

.skill-sparkle {
  opacity: 0;
  color: var(--orange);
  font-size: 0.8rem;
  transition: var(--transition-fast);
}

li:hover .skill-sparkle {
  opacity: 1;
  animation: sparkle 1s ease-in-out infinite;
}

@keyframes sparkle {
  0%, 100% { transform: scale(0) rotate(0deg); opacity: 0; }
  50% { transform: scale(1) rotate(180deg); opacity: 1; }
}

ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

.skill-category:hover {
  transform: translateY(-8px) scale(1.02);
  box-shadow: var(--glow-strong), 0 25px 50px rgba(0, 0, 0, 0.4);
  border-color: var(--orange);
}

/* Staggered animations */
.skill-0 { animation: fadeInUp 0.6s ease backwards; }
.skill-1 { animation: fadeInUp 0.6s ease 0.1s backwards; }
.skill-2 { animation: fadeInUp 0.6s ease 0.2s backwards; }
.skill-3 { animation: fadeInUp 0.6s ease 0.3s backwards; }

@media (max-width: 640px) {
  .skills-grid {
    grid-template-columns: 1fr;
  }
}
</style>