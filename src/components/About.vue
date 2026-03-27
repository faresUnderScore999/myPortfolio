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

      <img
        class="profile-photo"
        src="https://media.licdn.com/dms/image/v2/D5603AQHzEimaHye1uw/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1728967101373?e=1776297600&v=beta&t=uMR5IOiiFm9-V8UKDjBWpFTRuzi14ozUJwGt8BnglxY"
        alt="Fares Ben Ali profile photo"
        loading="lazy"
      />
    </div>
    <div class="meta">
      <span>📍 Tunis, Tunisia</span>
      <span>🗣️ Arabic · French · English</span>
      <span>✅ Available for opportunities</span>
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
}

.intro-layout {
  display: grid;
  grid-template-columns: 1fr auto;
  align-items: center;
  gap: 1.5rem;
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
  margin-bottom: 1rem;
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
}

h1 {
  margin: 0;
  font-size: clamp(1.8rem, 4vw, 3rem);
  color: var(--white);
}

.lead {
  margin-top: 1rem;
  font-size: 1.05rem;
  line-height: 1.8;
  max-width: 900px;
}

.meta {
  margin-top: 1.4rem;
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.meta span {
  padding: 0.35rem 0.65rem;
  border-radius: 8px;
  background: rgba(229, 229, 229, 0.08);
  border: 1px solid var(--line);
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .intro-layout {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .intro-text {
    order: 2;
  }

  .profile-photo {
    order: 1;
  }

  .profile-photo {
    width: 96px;
    height: 96px;
  }

  .meta {
    justify-content: center;
  }
}
</style>