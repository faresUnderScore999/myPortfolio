<template>
  <section id="experience" class="experience">
    <h2>💼 Experience</h2>

    <article class="timeline-item">
      <h3>🚀 Full Stack Developer Intern — Audasoft Technology</h3>
      <p class="period">Apr 2024 — Sep 2024</p>
      <ul>
        <li>Built an e-learning platform using Vue.js/Nuxt.js for frontend and Go (Gin) for backend.</li>
        <li>Implemented dashboards for students and teachers, course management, and live session planning.</li>
        <li>Integrated realtime interactions with WebRTC and notification/feedback systems.</li>
        <li>Worked on scalable data handling and reliable backend services.</li>
      </ul>
    </article>

    <article class="timeline-item">
      <h3>🏍️ Motorcycle Mechanic (Freelance)</h3>
      <p class="period">2024 — Present</p>
      <ul>
        <li>Diagnose and repair complex mechanical/electrical issues (STVA, sensors, regulators, injectors).</li>
        <li>Read and apply official service manuals and electrical schematics.</li>
        <li>Use practical diagnostic tools (multimeter, oscilloscope) and welding techniques.</li>
      </ul>
    </article>
  </section>
</template>

<script>
export default {
  name: 'Experience'
}
</script>

<style scoped>
.experience {
  background: color-mix(in srgb, var(--panel) 90%, transparent);
  border-radius: 16px;
  padding: 2.2rem 1.4rem;
  box-shadow: var(--glow), 0 10px 30px rgba(0, 0, 0, 0.35);
}

h2 {
  margin-top: 0;
  text-align: center;
}

.timeline-item {
  border: 1px solid color-mix(in srgb, var(--prussian-blue) 20%, var(--alabaster-grey));
  border-radius: 12px;
  padding: 1rem;
  margin-bottom: 1rem;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
}

.timeline-item:last-child {
  margin-bottom: 0;
}

.timeline-item:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 20px rgba(20, 33, 61, 0.16);
  border-color: var(--orange);
}

h3 {
  margin: 0 0 0.3rem;
  color: var(--orange);
}

.period {
  margin: 0 0 0.8rem;
  color: var(--text-soft);
  font-size: 0.95rem;
}

li {
  color: var(--text-soft);
}

ul {
  margin: 0;
  padding-left: 1.1rem;
}
</style>