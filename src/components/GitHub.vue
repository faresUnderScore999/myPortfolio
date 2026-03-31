<template>
  <section id="github" class="github">
    <h2>🐙 GitHub Highlights</h2>

    <p v-if="loading" class="state">Loading GitHub data...</p>
    <p v-else-if="error" class="state error">{{ error }}</p>

    <template v-else>
      <article v-if="profile" class="profile-card">
        <img :src="profile.avatar_url" :alt="`${profile.login} avatar`" class="avatar" loading="lazy" />

        <div class="profile-text">
          <h3>{{ profile.name || profile.login }}</h3>
          <p class="bio">{{ profile.bio || 'Full-stack developer building practical apps.' }}</p>

          <div class="stats">
            <span>📦 {{ profile.public_repos }} repos</span>
            <span>⭐ {{ profile.followers }} followers</span>
            <span>👥 {{ profile.following }} following</span>
          </div>

          <a :href="profile.html_url" target="_blank" rel="noopener noreferrer" class="profile-link">
            Open profile ↗
          </a>
        </div>
      </article>

      <div v-if="repos.length" class="repo-grid">
        <article v-for="repo in repos" :key="repo.id" class="repo-item">
          <h4>
            <a :href="repo.html_url" target="_blank" rel="noopener noreferrer">
              {{ repo.name }}
            </a>
          </h4>

          <p>{{ shortDescription(repo.description) }}</p>

          <div class="repo-meta">
            <span v-if="repo.language">🧠 {{ repo.language }}</span>
            <span>⭐ {{ repo.stargazers_count }}</span>
            <span>🍴 {{ repo.forks_count }}</span>
          </div>
        </article>
      </div>
    </template>
  </section>
</template>

<script>
export default {
  name: 'GitHub',
  props: {
    profile: {
      type: Object,
      default: null
    },
    repos: {
      type: Array,
      default: () => []
    },
    loading: {
      type: Boolean,
      default: false
    },
    error: {
      type: String,
      default: ''
    }
  },
  methods: {
    shortDescription(text) {
      if (!text) return 'No description provided.';
      const normalized = String(text).replace(/\n+/g, ' ').trim();
      return normalized.length > 120 ? `${normalized.slice(0, 120)}...` : normalized;
    }
  }
};
</script>

<style scoped>
.github {
  background: color-mix(in srgb, var(--panel) 90%, transparent);
  border-radius: 16px;
  padding: 2.2rem 1.4rem;
  box-shadow: var(--glow), 0 10px 30px rgba(0, 0, 0, 0.35);
}

h2 {
  margin-top: 0;
  text-align: center;
}

.state {
  text-align: center;
  color: var(--text-soft);
}

.state.error {
  color: #ff9aa2;
}

.profile-card {
  border: 1px solid color-mix(in srgb, var(--prussian-blue) 20%, var(--alabaster-grey));
  border-radius: 12px;
  padding: 1rem;
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 1rem;
  margin-bottom: 1rem;
  background: color-mix(in srgb, var(--panel-strong) 80%, transparent);
}

.avatar {
  width: 88px;
  height: 88px;
  border-radius: 999px;
  border: 2px solid var(--orange);
}

.profile-text h3 {
  margin: 0;
  color: var(--orange);
}

.bio {
  margin: 0.5rem 0;
  color: var(--text-soft);
}

.stats {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  font-size: 0.92rem;
}

.profile-link {
  display: inline-block;
  margin-top: 0.8rem;
  font-weight: 600;
}

.repo-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
  gap: 0.9rem;
}

.repo-item {
  border: 1px solid color-mix(in srgb, var(--prussian-blue) 20%, var(--alabaster-grey));
  border-radius: 12px;
  padding: 0.95rem;
  background: color-mix(in srgb, var(--panel-strong) 70%, transparent);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.repo-item:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 20px rgba(20, 33, 61, 0.18);
  border-color: var(--orange);
}

.repo-item h4 {
  margin: 0;
}

.repo-item p {
  color: var(--text-soft);
  margin: 0.6rem 0;
  min-height: 42px;
}

.repo-meta {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  font-size: 0.85rem;
}

@media (max-width: 640px) {
  .profile-card {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .avatar {
    margin: 0 auto;
  }

  .stats {
    justify-content: center;
  }
}
</style>