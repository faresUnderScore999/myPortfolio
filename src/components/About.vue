<template>
  <section id="about" class="about card">
    <div class="intro-layout">
      <div class="intro-text">
        <p class="eyebrow">🛠️ Full Stack Developer</p>
        <h1>Hi, I'm Fares Ben Ali</h1>
        <p class="lead">
          Passionate about web development, electronics, and technical problem-solving. I build modern full-stack apps using Vue/Nuxt, Node.js, and Go (Gin), and I enjoy turning complex ideas into practical, reliable solutions.
        </p>
      </div>
      <div class="photo-wrapper">
        <img
          class="profile-photo"
          src="https://media.licdn.com/dms/image/v2/D5603AQHzEimaHye1uw/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1728967101373?e=1776297600&v=beta&t=uMR5IOiiFm9-V8UKDjBWpFTRuzi14ozUJwGt8BnglxY"
          alt="Fares Ben Ali profile photo"
          loading="lazy"
        />
        <div class="photo-ring"></div>
      </div>
    </div>
    <div class="meta">
      <span class="meta-item">📍 Tunis, Tunisia</span>
      <span class="meta-item">🗣️ Arabic · French · English</span>
      <span class="meta-item available">✅ Available for opportunities</span>
    </div>
  </section>
</template>

<script>
export default {
  name: 'About'
}
</script>

<style scoped>
.card {
  background: linear-gradient(160deg, color-mix(in srgb, var(--panel-strong) 85%, var(--black)), #141d3a);
  color: var(--alabaster-grey);
  border: 1px solid var(--line);
  border-radius: 18px;
  padding: 2.5rem 2rem;
  box-shadow: var(--glow), 0 20px 45px rgba(0, 0, 0, 0.45);
  transition: var(--transition-medium);
}

.card:hover {
  box-shadow: var(--glow-strong), 0 25px 50px rgba(0, 0, 0, 0.5);
  transform: translateY(-2px);
}

.intro-layout {
  display: grid;
  grid-template-columns: 1fr auto;
  align-items: center;
  gap: 2rem;
}

.intro-text {
  min-width: 0;
}

.eyebrow {
  display: inline-block;
  padding: 0.35rem 0.8rem;
  border-radius: 999px;
  background: rgba(252, 163, 17, 0.2);
  color: var(--orange);
  font-size: 0.85rem;
  font-weight: 600;
  margin-bottom: 1rem;
  border: 1px solid rgba(252, 163, 17, 0.3);
}

.photo-wrapper {
  position: relative;
  display: inline-block;
}

.profile-photo {
  width: 150px;
  height: 150px;
  object-fit: cover;
  object-position: center top;
  border-radius: 999px;
  border: 3px solid var(--orange);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.35);
  margin-inline: auto;
  transition: var(--transition-medium);
  position: relative;
  z-index: 1;
}

.photo-ring {
  position: absolute;
  top: -8px;
  left: -8px;
  right: -8px;
  bottom: -8px;
  border-radius: 50%;
  border: 2px solid var(--orange);
  opacity: 0.4;
  animation: ring-pulse 3s ease-in-out infinite;
}

@keyframes ring-pulse {
  0%, 100% {
    transform: scale(1);
    opacity: 0.4;
  }
  50% {
    transform: scale(1.05);
    opacity: 0.2;
  }
}

.photo-wrapper:hover .profile-photo {
  transform: scale(1.05);
  box-shadow: var(--glow-strong), 0 15px 35px rgba(0, 0, 0, 0.4);
}

h1 {
  margin: 0;
  font-size: clamp(1.8rem, 4vw, 3rem);
  color: var(--white);
  line-height: 1.2;
}

.lead {
  margin-top: 1rem;
  font-size: 1.05rem;
  line-height: 1.8;
  max-width: 900px;
  color: var(--text-soft);
}

.meta {
  margin-top: 1.4rem;
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.meta-item {
  padding: 0.35rem 0.65rem;
  border-radius: 8px;
  background: rgba(229, 229, 229, 0.08);
  border: 1px solid var(--line);
  font-size: 0.9rem;
  transition: var(--transition-fast);
}

.meta-item:hover {
  background: rgba(252, 163, 17, 0.1);
  border-color: var(--orange);
}

.meta-item.available {
  background: rgba(34, 197, 94, 0.15);
  border-color: rgba(34, 197, 94, 0.4);
  color: #4ade80;
}

.meta-item.available:hover {
  background: rgba(34, 197, 94, 0.25);
  box-shadow: 0 0 15px rgba(34, 197, 94, 0.2);
}

@media (max-width: 768px) {
  .intro-layout {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .intro-text {
    order: 2;
  }

  .photo-wrapper {
    order: 1;
  }

  .profile-photo {
    width: 120px;
    height: 120px;
  }

  .meta {
    justify-content: center;
  }

  .meta-item {
    font-size: 0.85rem;
  }
}
</style>