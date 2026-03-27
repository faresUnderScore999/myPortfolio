<template>
  <section class="project-details is-visible" id="project-details">
    <button type="button" class="back-btn" @click.prevent="$emit('back')">← Back to projects</button>

    <div v-if="project" class="details-content">
      <h2>{{ project.emoji }} {{ project.title }}</h2>

      <div class="gallery" v-if="project.imageurl?.length">
        <img
          :src="project.imageurl[activeImage]"
          :alt="`${project.title} screenshot ${activeImage + 1}`"
          class="main-image"
          loading="lazy"
        />

        <div class="thumbs" v-if="project.imageurl.length > 1">
          <button
            v-for="(image, index) in project.imageurl"
            :key="`${project.title}-thumb-${index}`"
            type="button"
            class="thumb"
            :class="{ active: index === activeImage }"
            @click="activeImage = index"
          >
            <img :src="image" :alt="`${project.title} thumbnail ${index + 1}`" loading="lazy" />
          </button>
        </div>
      </div>

      <p class="description">{{ project.description }}</p>

      <a v-if="project.link" :href="project.link" target="_blank" rel="noopener noreferrer" class="visit-link">
        Visit project ↗
      </a>
    </div>

    <p v-else class="empty">Project not found.</p>
  </section>
</template>

<script>
export default {
  name: 'ProjectDetails',
  props: {
    project: {
      type: Object,
      default: null
    }
  },
  emits: ['back'],
  data() {
    return {
      activeImage: 0
    };
  },
  watch: {
    project: {
      immediate: true,
      handler() {
        this.activeImage = 0;
      }
    }
  }
}
</script>

<style scoped>
.project-details {
  background: color-mix(in srgb, var(--panel) 92%, transparent);
  border-radius: 16px;
  padding: 2rem 1.2rem;
  box-shadow: var(--glow), 0 10px 30px rgba(0, 0, 0, 0.35);
}

.back-btn {
  border: 1px solid var(--line);
  background: transparent;
  color: var(--orange);
  border-radius: 10px;
  padding: 0.45rem 0.75rem;
  font-weight: 600;
  cursor: pointer;
  margin-bottom: 1rem;
}

.details-content h2 {
  margin-top: 0;
  color: var(--orange);
}

.gallery {
  margin-bottom: 1rem;
}

.main-image {
  width: 100%;
  max-height: 460px;
  object-fit: contain;
  border-radius: 12px;
  border: 1px solid var(--line);
  background: color-mix(in srgb, var(--panel-strong) 70%, transparent);
}

.thumbs {
  margin-top: 0.6rem;
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.thumb {
  padding: 0;
  border: 1px solid transparent;
  background: transparent;
  border-radius: 8px;
  overflow: hidden;
  cursor: pointer;
}

.thumb.active {
  border-color: var(--orange);
}

.thumb img {
  width: 88px;
  height: 56px;
  object-fit: cover;
  display: block;
}

.description {
  color: var(--text-soft);
  line-height: 1.8;
  white-space: pre-line;
}

.visit-link {
  display: inline-block;
  margin-top: 0.8rem;
  color: var(--orange);
  font-weight: 700;
}

.empty {
  color: var(--text-soft);
}
</style>