<template>
  <section id="contact" class="contact">
    <h2>📬 Contact</h2>
    <p>Open to full-stack roles, freelance projects, and technical collaborations.</p>

    <div class="contact-grid">
      <a href="mailto:benalifares999@gmail.com">✉️ benalifares999@gmail.com</a>
      <a href="tel:+21651767126">📞 +216 51 767 126</a>
      <a href="https://github.com/faresUnderScore999" target="_blank" rel="noopener noreferrer">🐙 GitHub</a>
      <a href="https://www.linkedin.com/in/fares-ben-ali-1060872a4/" target="_blank" rel="noopener noreferrer">💼 LinkedIn</a>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Contact'
}
</script>

<style scoped>
.contact {
  background: linear-gradient(145deg, color-mix(in srgb, var(--panel) 86%, var(--black)), #101a33);
  border-radius: 16px;
  padding: 2.2rem 1.4rem;
  text-align: center;
  box-shadow: var(--glow), 0 10px 30px rgba(0, 0, 0, 0.35);
}

h2 {
  margin-top: 0;
}

p {
  color: var(--text-soft);
}

.contact-grid {
  margin-top: 1rem;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 0.7rem;
}

.contact-grid a {
  display: block;
  padding: 0.75rem 0.8rem;
  border-radius: 10px;
  background: color-mix(in srgb, var(--panel-strong) 84%, transparent);
  color: var(--alabaster-grey);
  text-decoration: none;
  border: 1px solid var(--line);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.contact-grid a:hover {
  transform: translateY(-3px);
  box-shadow: var(--glow), 0 8px 18px rgba(20, 33, 61, 0.35);
  border-color: var(--orange);
}
</style>