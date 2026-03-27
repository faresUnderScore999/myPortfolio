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
        <img
          v-if="project.imageurl?.length"
          :src="project.imageurl[0]"
          :alt="`${project.title} preview`"
          class="project-image"
          loading="lazy"
        />

        <h3>{{ project.emoji }} {{ project.title }}</h3>
        <p>{{ shortDescription(project.description) }}</p>

        <button type="button" class="details-btn">View details</button>
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
      if (!text) return '';
      const normalized = String(text).replace(/\n+/g, ' ').trim();
      return normalized.length > 140 ? `${normalized.slice(0, 140)}...` : normalized;
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
}

.empty-state {
  text-align: center;
  color: var(--text-soft);
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(250px, 1fr));
  gap: 1rem;
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
  border: 1px solid color-mix(in srgb, var(--prussian-blue) 20%, var(--alabaster-grey));
  border-radius: 12px;
  padding: 1rem;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  cursor: pointer;
  background: color-mix(in srgb, var(--panel-strong) 80%, transparent);
}

.project-item:hover,
.project-item:focus-visible {
  transform: translateY(-6px);
  box-shadow: 0 12px 22px rgba(20, 33, 61, 0.16);
  border-color: var(--orange);
  outline: none;
}

.project-image {
  width: 100%;
  height: 160px;
  object-fit: cover;
  border-radius: 10px;
  border: 1px solid var(--line);
  margin-bottom: 0.75rem;
}

h3 {
  margin-top: 0;
  color: var(--orange);
}

p {
  margin-bottom: 0.8rem;
  color: var(--text-soft);
}

.details-btn {
  border: 1px solid var(--line);
  background: transparent;
  color: var(--orange);
  border-radius: 8px;
  padding: 0.45rem 0.7rem;
  font-weight: 600;
  cursor: pointer;
}
</style>