<template>
  <section id="skills" class="skills">
    <h2>🧩 Skills</h2>
    <div class="skills-grid">
      <article class="skill-category">
        <h3>🎨 Frontend</h3>
        <ul>
          <li>Vue.js</li>
          <li>Nuxt.js</li>
          <li>JavaScript (ES6+)</li>
          <li>HTML5 / CSS3</li>
        </ul>
      </article>

      <article class="skill-category">
        <h3>⚙️ Backend</h3>
        <ul>
          <li>Node.js / Express</li>
          <li>Go (Gin Framework)</li>
          <li>REST APIs</li>
          <li>JWT Authentication</li>
          <li>WebSocket / WebRTC</li>
        </ul>
      </article>

      <article class="skill-category">
        <h3>🧰 Tools</h3>
        <ul>
          <li>Git / GitHub</li>
          <li>Docker</li>
          <li>Vercel / Render</li>
          <li>MongoDB</li>
          <li>Python Automation</li>
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
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 1rem;
}

.skill-category {
  border: 1px solid color-mix(in srgb, var(--prussian-blue) 20%, var(--alabaster-grey));
  border-radius: 12px;
  padding: 1rem;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
}

.skill-category:hover {
  transform: translateY(-6px);
  box-shadow: 0 12px 22px rgba(20, 33, 61, 0.16);
  border-color: var(--orange);
}

h3 {
  margin-top: 0;
  color: var(--orange);
}

li {
  color: var(--text-soft);
}

ul {
  margin: 0;
  padding-left: 1rem;
}
</style>