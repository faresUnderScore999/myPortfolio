<template>
  <section id="skills" class="skills">
    <h2>🧩 Skills</h2>
    <div class="skills-grid">
      <article class="skill-category">
        <div class="category-icon">🎨</div>
        <h3>Frontend</h3>
        <ul>
          <li>Vue.js / Nuxt.js</li>
          <li>React.js</li>
          <li>JavaScript (ES6+)</li>
          <li>HTML5 / CSS3</li>
          <li>TypeScript</li>
        </ul>
      </article>
      <article class="skill-category">
        <div class="category-icon">⚙️</div>
        <h3>Backend</h3>
        <ul>
          <li>Node.js / Express</li>
          <li>Go (Gin Framework)</li>
          <li>Spring Boot</li>
          <li>JEE / Java</li>
          <li>Symfony 6.4</li>
          <li>REST APIs / GraphQL</li>
        </ul>
      </article>
      <article class="skill-category">
        <div class="category-icon">🧰</div>
        <h3>Tools & DevOps</h3>
        <ul>
          <li>Docker</li>
          <li>Git / GitHub</li>
          <li>Postman API</li>
          <li>Selenium WebDriver</li>
          <li>SQL / MongoDB</li>
        </ul>
      </article>
      <article class="skill-category">
        <div class="category-icon">🔒</div>
        <h3>Other Skills</h3>
        <ul>
          <li>WebRTC</li>
          <li>Cybersecurity</li>
          <li>Méthodes Agiles</li>
          <li>Routeurs Cisco</li>
          <li>Python</li>
        </ul>
      </article>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Skills'
}
</script>

<style scoped>
.skills {
  background: color-mix(in srgb, var(--panel) 90%, transparent);
  border-radius: 16px;
  padding: 2.2rem 1.4rem;
  box-shadow: var(--glow), 0 10px 30px rgba(0, 0, 0, 0.35);
}

h2 {
  text-align: center;
  margin-top: 0;
  color: var(--white);
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.25rem;
}

.skill-category {
  border: 1px solid var(--line);
  border-radius: 16px;
  padding: 1.5rem;
  transition: var(--transition-medium);
  background: linear-gradient(180deg, rgba(20, 33, 61, 0.5), rgba(11, 19, 40, 0.7));
  position: relative;
  overflow: hidden;
}

.skill-category::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--orange), transparent);
  opacity: 0;
  transition: var(--transition-medium);
}

.skill-category:hover {
  transform: translateY(-6px);
  box-shadow: var(--glow-strong), 0 15px 35px rgba(0, 0, 0, 0.35);
  border-color: var(--orange);
}

.skill-category:hover::before {
  opacity: 1;
}

.category-icon {
  font-size: 1.75rem;
  margin-bottom: 0.5rem;
}

h3 {
  margin-top: 0;
  margin-bottom: 1rem;
  color: var(--orange);
  font-size: 1.1rem;
}

li {
  color: var(--text-soft);
  margin-bottom: 0.4rem;
  position: relative;
  padding-left: 1rem;
}

li::before {
  content: '▹';
  position: absolute;
  left: 0;
  color: var(--orange);
}

ul {
  margin: 0;
  padding-left: 0;
  list-style: none;
}
</style>