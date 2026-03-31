<template>
  <section id="projects" class="projects">
    <div class="section-glow"></div>
    <h2>
      <span class="section-icon">📂</span>
      <span class="section-title">Projects</span>
    </h2>
    <p v-if="!projects?.length" class="empty-state">
      No projects available right now.
    </p>
    <div v-else class="projects-grid">
      <article
        v-for="(project, index) in projects"
        :key="`${project.title}-${index}`"
        class="project-item"
        :class="`project-${index}`"
        role="button"
        tabindex="0"
        @click="$emit('open-project', index)"
        @keydown.enter="$emit('open-project', index)"
      >
        <div class="project-card-glow"></div>
        <div class="image-container">
          <div class="image-shine"></div>
          <img
            v-if="project.imageurl?.length"
            :src="project.imageurl[0]"
            :alt="`${project.title} preview`"
            class="project-image"
            loading="lazy"
          />
          <div class="image-overlay">
            <div class="view-icon-wrapper">
              <span class="view-icon">👁️</span>
              <span class="view-text">View Details</span>
            </div>
          </div>
          <div class="project-badge" v-if="project.link">
            <span>🚀</span> Live
          </div>
        </div>
        <div class="project-content">
          <h3>{{ project.emoji }} {{ project.title }}</h3>
          <p>{{ shortDescription(project.description) }}</p>
          <div class="project-footer">
            <span class="details-btn">
              <span>Explore</span>
              <span class="arrow">→</span>
            </span>
          </div>
        </div>
        <div class="card-border-glow"></div>
      </article>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Projects',
  props: {
    projects: {
      type: Array,
      default: () => []
    }
  },
  emits: ['open-project'],
  methods: {
    shortDescription(text) {
      if (!text) return ''
      const normalized = String(text).replace(/\n+/g, ' ').trim()
      return normalized.length > 140 ? `${normalized.slice(0, 140)}...` : normalized
    }
  }
}
</script>

<style scoped>
.projects {
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
  left: 50%;
  transform: translateX(-50%);
  width: 400px;
  height: 200px;
  background: radial-gradient(ellipse, rgba(252, 163, 17, 0.15), transparent 70%);
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

.empty-state {
  text-align: center;
  color: var(--text-soft);
  font-size: 1.1rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(300px, 1fr));
  gap: 1.75rem;
  position: relative;
  z-index: 1;
}

@media (max-width: 1100px) {
  .projects-grid {
    grid-template-columns: repeat(2, minmax(280px, 1fr));
  }
}

@media (max-width: 700px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
}

.project-item {
  border: 1px solid var(--line);
  border-radius: 20px;
  padding: 0;
  transition: var(--transition-medium);
  background: linear-gradient(180deg, rgba(20, 33, 61, 0.6), rgba(11, 19, 40, 0.85));
  position: relative;
  overflow: hidden;
  cursor: pointer;
}

.project-card-glow {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: linear-gradient(90deg, transparent, var(--orange), transparent);
  opacity: 0;
  transition: var(--transition-medium);
}

.project-item:hover .project-card-glow {
  opacity: 1;
}

.card-border-glow {
  position: absolute;
  inset: 0;
  border-radius: 20px;
  background: linear-gradient(135deg, var(--orange), transparent, var(--orange));
  opacity: 0;
  transition: var(--transition-medium);
  z-index: -1;
}

.project-item:hover {
  transform: translateY(-10px) scale(1.02);
  box-shadow: 
    var(--glow-intense),
    0 30px 60px rgba(0, 0, 0, 0.5);
  border-color: var(--orange);
}

.project-item:hover .card-border-glow {
  opacity: 0.5;
}

.image-container {
  position: relative;
  border-radius: 20px 20px 0 0;
  overflow: hidden;
  margin-bottom: 0;
}

.image-shine {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, transparent 40%, rgba(255, 255, 255, 0.1) 50%, transparent 60%);
  transform: translateX(-100%);
  transition: var(--transition-slow);
  pointer-events: none;
  z-index: 2;
}

.project-item:hover .image-shine {
  transform: translateX(100%);
}

.project-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
  display: block;
  transition: var(--transition-medium);
}

.image-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(5, 7, 15, 0.95), rgba(5, 7, 15, 0.3));
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: var(--transition-medium);
}

.view-icon-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  transform: translateY(20px);
  transition: var(--transition-medium);
}

.view-icon {
  font-size: 2.5rem;
  filter: grayscale(1);
  transition: var(--transition-fast);
}

.view-text {
  color: var(--orange);
  font-weight: 600;
  font-size: 0.95rem;
}

.project-item:hover .image-overlay {
  opacity: 1;
}

.project-item:hover .view-icon-wrapper {
  transform: translateY(0);
}

.project-item:hover .view-icon {
  filter: grayscale(0);
  animation: pulse 1s ease-in-out infinite;
}

.project-badge {
  position: absolute;
  top: 12px;
  right: 12px;
  background: rgba(34, 197, 94, 0.2);
  border: 1px solid rgba(34, 197, 94, 0.5);
  color: #4ade80;
  padding: 0.3rem 0.7rem;
  border-radius: 20px;
  font-size: 0.75rem;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 0.3rem;
}

.project-content {
  padding: 1.25rem;
}

h3 {
  margin: 0 0 0.5rem;
  color: var(--orange);
  font-size: 1.2rem;
  font-weight: 600;
}

p {
  margin: 0 0 1rem;
  color: var(--text-soft);
  font-size: 0.95rem;
  line-height: 1.6;
}

.project-footer {
  display: flex;
  justify-content: flex-end;
}

.details-btn {
  color: var(--orange);
  font-weight: 600;
  font-size: 0.9rem;
  display: flex;
  align-items: center;
  gap: 0.4rem;
  transition: var(--transition-fast);
}

.arrow {
  transition: var(--transition-fast);
}

.project-item:hover .details-btn {
  text-shadow: 0 0 15px rgba(252, 163, 17, 0.6);
}

.project-item:hover .arrow {
  transform: translateX(5px);
}

/* Staggered animation */
.project-0 { animation: fadeInUp 0.6s ease backwards; }
.project-1 { animation: fadeInUp 0.6s ease 0.1s backwards; }
.project-2 { animation: fadeInUp 0.6s ease 0.2s backwards; }
.project-3 { animation: fadeInUp 0.6s ease 0.3s backwards; }
.project-4 { animation: fadeInUp 0.6s ease 0.4s backwards; }
.project-5 { animation: fadeInUp 0.6s ease 0.5s backwards; }
</style>