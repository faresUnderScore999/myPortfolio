<template>
  <section id="projects" class="projects">
    <h2>📂 Projects</h2>
    <p v-if="!projects?.length" class="empty-state">
      No projects available right now.
    </p>
    <div v-else class="projects-grid">
      <article
        v-for="(project, index) in projects"
        :key="`${project.title}-${index}`"
        class="project-item"
        role="button"
        tabindex="0"
        @click="$emit('open-project', index)"
        @keydown.enter="$emit('open-project', index)"
      >
        <div class="image-container">
          <img
            v-if="project.imageurl?.length"
            :src="project.imageurl[0]"
            :alt="`${project.title} preview`"
            class="project-image"
            loading="lazy"
          />
          <div class="image-overlay">
            <span class="view-icon">👁️</span>
          </div>
        </div>
        <h3>{{ project.emoji }} {{ project.title }}</h3>
        <p>{{ shortDescription(project.description) }}</p>
        <div class="project-footer">
          <span class="details-btn">View details →</span>
        </div>
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
  border-radius: 16px;
  padding: 2.2rem 1.4rem;
  box-shadow: var(--glow), 0 10px 30px rgba(0, 0, 0, 0.35);
}

h2 {
  margin-top: 0;
  text-align: center;
  color: var(--white);
}

.empty-state {
  text-align: center;
  color: var(--text-soft);
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(280px, 1fr));
  gap: 1.5rem;
}

@media (max-width: 980px) {
  .projects-grid {
    grid-template-columns: repeat(2, minmax(250px, 1fr));
  }
}

@media (max-width: 640px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
}

.project-item {
  border: 1px solid var(--line);
  border-radius: 16px;
  padding: 1.25rem;
  transition: var(--transition-medium);
  cursor: pointer;
  background: linear-gradient(180deg, rgba(20, 33, 61, 0.6), rgba(11, 19, 40, 0.8));
  position: relative;
  overflow: hidden;
}

.project-item::before {
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

.project-item:hover,
.project-item:focus-visible {
  transform: translateY(-8px);
  box-shadow: var(--glow-strong), 0 20px 40px rgba(0, 0, 0, 0.4);
  border-color: var(--orange);
  outline: none;
}

.project-item:hover::before,
.project-item:focus-visible::before {
  opacity: 1;
}

.image-container {
  position: relative;
  border-radius: 12px;
  overflow: hidden;
  margin-bottom: 1rem;
}

.project-image {
  width: 100%;
  height: 180px;
  object-fit: cover;
  display: block;
  transition: var(--transition-medium);
}

.image-overlay {
  position: absolute;
  inset: 0;
  background: rgba(252, 163, 17, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: var(--transition-medium);
}

.view-icon {
  font-size: 2rem;
  filter: grayscale(1);
  transition: var(--transition-fast);
}

.project-item:hover .image-overlay {
  opacity: 1;
}

.project-item:hover .project-image {
  transform: scale(1.05);
}

.project-item:hover .view-icon {
  filter: grayscale(0);
  transform: scale(1.1);
}

h3 {
  margin-top: 0;
  color: var(--orange);
  font-size: 1.15rem;
  margin-bottom: 0.5rem;
}

p {
  margin-bottom: 1rem;
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
  transition: var(--transition-fast);
}

.project-item:hover .details-btn {
  text-shadow: 0 0 10px rgba(252, 163, 17, 0.5);
}
</style>