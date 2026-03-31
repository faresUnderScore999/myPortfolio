<template>
  <div id="app">
    <Header />
    <main v-if="!selectedProject">
      <About />
      <Education />
      <Skills :github-repos="githubRepos" :github-loading="githubLoading" :github-error="githubError" />
      <Projects :projects="projects" @open-project="openProject" />
      <GitHub :profile="githubProfile" :repos="featuredGithubRepos" :loading="githubLoading" :error="githubError" />
      <Experience />
      <Contact />
    </main>
    <main v-else class="details-view">
      <ProjectDetails :project="selectedProject" @back="goHome" />
    </main>
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import About from './components/About.vue'
import Education from './components/Education.vue'
import GitHub from './components/GitHub.vue'
import Skills from './components/Skills.vue'
import Experience from './components/Experience.vue'
import Projects from './components/Projects.vue'
import ProjectDetails from './components/ProjectDetails.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    About,
    Education,
    GitHub,
    Skills,
    Experience,
    Projects,
    ProjectDetails,
    Contact,
    Footer
  },
  data() {
    return {
      observer: null,
      projects: [],
      selectedProject: null,
      githubProfile: null,
      githubRepos: [],
      featuredGithubRepos: [],
      githubLoading: false,
      githubError: ''
    }
  },
  async mounted() {
    await Promise.all([this.loadProjects(), this.loadGitHubData()])
    window.addEventListener('hashchange', this.handleHashRoute)
    this.handleHashRoute()
    if (!this.selectedProject) {
      this.$nextTick(() => this.setupSectionObserver())
    }
  },
  beforeUnmount() {
    window.removeEventListener('hashchange', this.handleHashRoute)
    if (this.observer) {
      this.observer.disconnect()
    }
  },
  methods: {
    async loadProjects() {
      try {
        const response = await fetch('/data.json')
        if (!response.ok) throw new Error('Failed to load data.json')
        this.projects = await response.json()
      } catch (error) {
        console.error(error)
        this.projects = []
      }
    },
    async loadGitHubData() {
      this.githubLoading = true
      this.githubError = ''
      try {
        const username = 'faresUnderScore999'
        const [profileResponse, reposResponse] = await Promise.all([
          fetch(`https://api.github.com/users/${username}`),
          fetch(`https://api.github.com/users/${username}/repos?sort=updated&per_page=30`)
        ])
        if (!profileResponse.ok || !reposResponse.ok) {
          throw new Error('Unable to load GitHub information right now.')
        }
        this.githubProfile = await profileResponse.json()
        const repos = await reposResponse.json()
        const nonForkRepos = repos.filter((repo) => !repo.fork && !repo.archived)
        const scoreRepo = (repo) => {
          const stars = repo?.stargazers_count || 0
          const forks = repo?.forks_count || 0
          const watchers = repo?.watchers_count || 0
          const size = repo?.size || 0
          return stars * 5 + forks * 3 + watchers * 2 + size * 0.01
        }
        const featured = [...nonForkRepos]
          .sort((a, b) => scoreRepo(b) - scoreRepo(a))
          .slice(0, 4)
        this.githubRepos = nonForkRepos
        this.featuredGithubRepos = featured
      } catch (error) {
        console.error(error)
        this.githubError = 'GitHub data is temporarily unavailable.'
        this.githubProfile = null
        this.githubRepos = []
        this.featuredGithubRepos = []
      } finally {
        this.githubLoading = false
      }
    },
    setupSectionObserver() {
      if (this.observer) {
        this.observer.disconnect()
      }
      this.observer = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add('is-visible')
              this.observer.unobserve(entry.target)
            }
          })
        },
        { threshold: 0.15 }
      )
      document.querySelectorAll('section').forEach((section) => {
        this.observer.observe(section)
      })
    },
    handleHashRoute() {
      const match = window.location.hash.match(/^#project\/(\d+)$/)
      if (match) {
        const index = Number(match[1])
        this.selectedProject = this.projects[index] || null
        window.scrollTo({ top: 0, behavior: 'smooth' })
      } else {
        this.selectedProject = null
        this.$nextTick(() => this.setupSectionObserver())
      }
    },
    openProject(index) {
      this.selectedProject = this.projects[index] || null
      window.location.hash = `project/${index}`
      window.scrollTo({ top: 0, behavior: 'smooth' })
    },
    goHome() {
      this.selectedProject = null
      const cleanUrl = `${window.location.pathname}${window.location.search}`
      window.history.pushState(null, '', cleanUrl)
      this.$nextTick(() => {
        this.setupSectionObserver()
        const projectsSection = document.getElementById('projects')
        projectsSection?.scrollIntoView({ behavior: 'smooth', block: 'start' })
      })
    }
  }
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background: transparent;
}

main {
  flex: 1;
  width: min(1200px, calc(100% - 2rem));
  margin: 1.25rem auto 0;
  padding-top: 1.5rem;
  /* add spacing below sticky header */
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

section {
  scroll-margin-top: 88px;
  padding: 40px 20px;
  margin: 0;
  max-width: 100%;
  border: 1px solid var(--line);
  opacity: 0.2;
  transform: translateY(24px) scale(0.99);
  transition: opacity 0.7s ease, transform 0.7s ease;
}

.details-view {
  align-items: stretch;
}

section.is-visible {
  opacity: 1;
  transform: translateY(0) scale(1);
}

@media (max-width: 768px) {
  main {
    width: calc(100% - 1rem);
    margin-top: 0.75rem;
  }

  section {
    padding: 28px 16px;
  }
}
</style>