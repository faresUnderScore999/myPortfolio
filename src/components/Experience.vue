<template>
  <section id="experience" class="experience">
    <h2>💼 Experience</h2>
    <div class="timeline">
      <article class="timeline-item">
        <div class="timeline-marker"></div>
        <div class="timeline-content">
          <h3>🚀 Full Stack Developer Intern — Audasoft Technology</h3>
          <p class="period">Apr 2024 — Sep 2024</p>
          <ul>
            <li>Built an e-learning platform using Vue.js/Nuxt.js for frontend and Go (Gin) for backend.</li>
            <li>Implemented dashboards for students and teachers, course management, and live session planning.</li>
            <li>Integrated realtime interactions with WebRTC and notification/feedback systems.</li>
            <li>Worked on scalable data handling and reliable backend services.</li>
          </ul>
        </div>
      </article>
      <article class="timeline-item">
        <div class="timeline-marker"></div>
        <div class="timeline-content">
          <h3>🏍️ Motorcycle Mechanic (Freelance)</h3>
          <p class="period">2024 — Present</p>
          <ul>
            <li>Diagnose and repair complex mechanical/electrical issues (STVA, sensors, regulators, injectors).</li>
            <li>Read and apply official service manuals and electrical schematics.</li>
            <li>Use practical diagnostic tools (multimeter, oscilloscope) and welding techniques.</li>
          </ul>
        </div>
      </article>
    </div>
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
  color: var(--white);
}

.timeline {
  position: relative;
  padding-left: 2rem;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 6px;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(180deg, var(--orange), var(--prussian-blue));
  border-radius: 2px;
}

.timeline-item {
  position: relative;
  margin-bottom: 1.5rem;
  padding: 1.25rem;
  border: 1px solid var(--line);
  border-radius: 16px;
  background: linear-gradient(180deg, rgba(20, 33, 61, 0.5), rgba(11, 19, 40, 0.7));
  transition: var(--transition-medium);
}

.timeline-item:last-child {
  margin-bottom: 0;
}

.timeline-item:hover {
  transform: translateX(8px);
  box-shadow: var(--glow-strong), 0 15px 35px rgba(0, 0, 0, 0.35);
  border-color: var(--orange);
}

.timeline-marker {
  position: absolute;
  left: -2rem;
  top: 1.5rem;
  width: 14px;
  height: 14px;
  background: var(--orange);
  border-radius: 50%;
  box-shadow: 0 0 10px var(--orange);
  transform: translateY(-50%);
}

.timeline-item:hover .timeline-marker {
  box-shadow: 0 0 20px var(--orange), 0 0 30px rgba(252, 163, 17, 0.5);
}

.timeline-content h3 {
  margin: 0 0 0.3rem;
  color: var(--orange);
  font-size: 1.1rem;
}

.period {
  margin: 0 0 0.8rem;
  color: var(--text-soft);
  font-size: 0.95rem;
  display: inline-block;
  padding: 0.2rem 0.6rem;
  background: rgba(252, 163, 17, 0.1);
  border-radius: 6px;
  font-weight: 500;
}

li {
  color: var(--text-soft);
  margin-bottom: 0.4rem;
}

li:last-child {
  margin-bottom: 0;
}

ul {
  margin: 0;
  padding-left: 1.1rem;
}

@media (max-width: 640px) {
  .timeline {
    padding-left: 1.5rem;
  }

  .timeline::before {
    left: 4px;
  }

  .timeline-marker {
    left: -1.5rem;
    width: 10px;
    height: 10px;
  }

  .timeline-item:hover {
    transform: translateY(-4px);
  }
}
</style>