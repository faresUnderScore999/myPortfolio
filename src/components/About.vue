<template>
  <section id="about" class="about card">
    <div class="card-glow"></div>
    <div class="intro-layout">
      <div class="intro-text">
        <p class="eyebrow">
          <span class="eyebrow-glow"></span>
          🛠️ Full Stack Developer
        </p>
        <h1>
          <span class="title-gradient">Hi, I'm Fares Ben Ali</span>
        </h1>
        <p class="lead">
          Passionate about web development, electronics, and technical problem-solving. 
          I build modern full-stack apps using Vue/Nuxt, Node.js, and Go (Gin), and I enjoy 
          turning complex ideas into practical, reliable solutions.
        </p>
        <div class="cta-buttons">
          <a href="#projects" class="btn-primary" @click.prevent="navigate('#projects')">
            <span>View My Work</span>
            <span class="btn-glow"></span>
          </a>
          <a href="#contact" class="btn-secondary" @click.prevent="navigate('#contact')">
            <span>Get In Touch</span>
          </a>
        </div>
      </div>
      <div class="photo-wrapper">
        <div class="photo-orb"></div>
        <div class="photo-ring-outer"></div>
        <div class="photo-ring-inner"></div>
        <img
          class="profile-photo"
          src="https://media.licdn.com/dms/image/v2/D5603AQHzEimaHye1uw/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1728967101373?e=1776297600&v=beta&t=uMR5IOiiFm9-V8UKDjBWpFTRuzi14ozUJwGt8BnglxY"
          alt="Fares Ben Ali profile photo"
          loading="lazy"
        />
        <div class="photo-sparkles">
          <span v-for="n in 6" :key="n" class="sparkle" :style="{ '--i': n }">✦</span>
        </div>
      </div>
    </div>
    <div class="meta">
      <span class="meta-item location">
        <span class="meta-icon">📍</span>
        <span>Tunis, Tunisia</span>
      </span>
      <span class="meta-item languages">
        <span class="meta-icon">🗣️</span>
        <span>Arabic · French · English</span>
      </span>
      <span class="meta-item available">
        <span class="pulse-dot"></span>
        <span>Available for opportunities</span>
      </span>
    </div>
  </section>
</template>

<script>
export default {
  name: 'About',
  methods: {
    navigate(hash) {
      window.location.hash = hash
      setTimeout(
        () =>
          window.scrollTo({
            top: document.querySelector(hash)?.offsetTop - 70 || 0,
            behavior: 'smooth'
          }),
        50
      )
    }
  }
}
</script>

<style scoped>
.card {
  background: linear-gradient(160deg, 
    rgba(20, 33, 61, 0.7), 
    rgba(11, 19, 40, 0.9)
  );
  color: var(--alabaster-grey);
  border: 1px solid var(--line);
  border-radius: 24px;
  padding: 3rem 2.5rem;
  box-shadow: 
    var(--glow),
    0 20px 60px rgba(0, 0, 0, 0.4),
    inset 0 1px 0 rgba(252, 163, 17, 0.1);
  position: relative;
  overflow: hidden;
  transition: var(--transition-medium);
}

.card:hover {
  box-shadow: 
    var(--glow-strong),
    0 30px 80px rgba(0, 0, 0, 0.5),
    inset 0 1px 0 rgba(252, 163, 17, 0.2);
  transform: translateY(-4px);
}

.card-glow {
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle at 30% 30%, rgba(252, 163, 17, 0.08), transparent 40%);
  pointer-events: none;
  animation: rotate 20s linear infinite;
}

.intro-layout {
  display: grid;
  grid-template-columns: 1fr auto;
  align-items: center;
  gap: 3rem;
  position: relative;
  z-index: 1;
}

.intro-text {
  min-width: 0;
}

.eyebrow {
  display: inline-block;
  padding: 0.4rem 1rem;
  border-radius: 999px;
  background: rgba(252, 163, 17, 0.15);
  color: var(--orange);
  font-size: 0.9rem;
  font-weight: 600;
  margin-bottom: 1.25rem;
  border: 1px solid rgba(252, 163, 17, 0.3);
  position: relative;
  overflow: hidden;
}

.eyebrow-glow {
  position: absolute;
  inset: 0;
  background: linear-gradient(90deg, transparent, rgba(252, 163, 17, 0.3), transparent);
  animation: shimmer 2s infinite;
}

.photo-wrapper {
  position: relative;
  display: inline-block;
  width: 180px;
  height: 180px;
}

.profile-photo {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center top;
  border-radius: 50%;
  border: 3px solid var(--orange);
  box-shadow: 
    0 0 30px rgba(252, 163, 17, 0.4),
    0 15px 40px rgba(0, 0, 0, 0.4);
  position: relative;
  z-index: 2;
  transition: var(--transition-medium);
}

.photo-orb {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 200px;
  height: 200px;
  background: radial-gradient(circle, rgba(252, 163, 17, 0.3), transparent 70%);
  animation: pulse 3s ease-in-out infinite;
  z-index: 1;
}

.photo-ring-outer {
  position: absolute;
  top: -15px;
  left: -15px;
  right: -15px;
  bottom: -15px;
  border: 2px solid var(--orange);
  border-radius: 50%;
  opacity: 0.3;
  animation: ring-rotate 10s linear infinite;
  z-index: 0;
}

.photo-ring-inner {
  position: absolute;
  top: -8px;
  left: -8px;
  right: -8px;
  bottom: -8px;
  border: 1px solid var(--orange);
  border-radius: 50%;
  opacity: 0.5;
  animation: ring-rotate 7s linear infinite reverse;
  z-index: 1;
}

@keyframes ring-rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

.photo-sparkles {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.sparkle {
  position: absolute;
  color: var(--orange);
  font-size: 1rem;
  animation: sparkle 2s ease-in-out infinite;
  opacity: 0;
}

.sparkle:nth-child(1) { top: 10%; left: 80%; animation-delay: 0s; }
.sparkle:nth-child(2) { top: 30%; left: 95%; animation-delay: 0.3s; }
.sparkle:nth-child(3) { top: 70%; left: 100%; animation-delay: 0.6s; }
.sparkle:nth-child(4) { top: 90%; left: 80%; animation-delay: 0.9s; }
.sparkle:nth-child(5) { top: 80%; left: 20%; animation-delay: 1.2s; }
.sparkle:nth-child(6) { top: 20%; left: 10%; animation-delay: 1.5s; }

@keyframes sparkle {
  0%, 100% { opacity: 0; transform: scale(0); }
  50% { opacity: 1; transform: scale(1); }
}

.photo-wrapper:hover .profile-photo {
  transform: scale(1.08);
  box-shadow: 
    var(--glow-intense),
    0 20px 50px rgba(0, 0, 0, 0.5);
}

.photo-wrapper:hover .photo-ring-outer,
.photo-wrapper:hover .photo-ring-inner {
  opacity: 0.8;
}

h1 {
  margin: 0;
  font-size: clamp(2rem, 5vw, 3.5rem);
  color: var(--white);
  line-height: 1.15;
  margin-bottom: 1rem;
}

.title-gradient {
  background: linear-gradient(135deg, var(--white) 0%, var(--orange) 50%, var(--white) 100%);
  background-size: 200% auto;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: gradientShift 4s ease infinite;
}

.lead {
  margin: 0 0 1.5rem;
  font-size: 1.1rem;
  line-height: 1.8;
  max-width: 600px;
  color: var(--text-soft);
}

.cta-buttons {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.btn-primary,
.btn-secondary {
  display: inline-flex;
  align-items: center;
  padding: 0.75rem 1.5rem;
  border-radius: 12px;
  font-weight: 600;
  font-size: 0.95rem;
  cursor: pointer;
  transition: var(--transition-medium);
  text-decoration: none;
  position: relative;
  overflow: hidden;
}

.btn-primary {
  background: linear-gradient(135deg, var(--orange), #ff6b35);
  color: var(--black);
  border: none;
  box-shadow: 0 4px 20px rgba(252, 163, 17, 0.4);
}

.btn-primary:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 30px rgba(252, 163, 17, 0.6);
}

.btn-glow {
  position: absolute;
  inset: 0;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
  transform: translateX(-100%);
  animation: btnShimmer 3s infinite;
}

@keyframes btnShimmer {
  100% { transform: translateX(100%); }
}

.btn-secondary {
  background: transparent;
  color: var(--orange);
  border: 1px solid var(--orange);
}

.btn-secondary:hover {
  background: rgba(252, 163, 17, 0.15);
  transform: translateY(-3px);
  box-shadow: 0 0 20px rgba(252, 163, 17, 0.3);
}

.meta {
  margin-top: 2rem;
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
  position: relative;
  z-index: 1;
}

.meta-item {
  padding: 0.5rem 0.85rem;
  border-radius: 12px;
  background: rgba(229, 229, 229, 0.05);
  border: 1px solid var(--line);
  font-size: 0.9rem;
  display: flex;
  align-items: center;
  gap: 0.4rem;
  transition: var(--transition-fast);
}

.meta-item:hover {
  background: rgba(252, 163, 17, 0.1);
  border-color: var(--orange);
  transform: translateY(-2px);
}

.meta-icon {
  font-size: 1rem;
}

.meta-item.available {
  background: rgba(34, 197, 94, 0.1);
  border-color: rgba(34, 197, 94, 0.4);
  color: #4ade80;
}

.pulse-dot {
  width: 8px;
  height: 8px;
  background: #4ade80;
  border-radius: 50%;
  animation: pulse 2s ease-in-out infinite;
  box-shadow: 0 0 10px #4ade80;
}

@media (max-width: 768px) {
  .intro-layout {
    grid-template-columns: 1fr;
    text-align: center;
    gap: 2rem;
  }

  .intro-text {
    order: 2;
  }

  .photo-wrapper {
    order: 1;
    width: 140px;
    height: 140px;
    margin: 0 auto;
  }

  .lead {
    max-width: 100%;
  }

  .cta-buttons {
    justify-content: center;
  }

  .meta {
    justify-content: center;
  }

  .card {
    padding: 2rem 1.5rem;
  }
}
</style>