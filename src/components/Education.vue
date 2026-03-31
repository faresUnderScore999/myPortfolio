<template>
  <section id="education" class="education">
    <h2>🎓 Education</h2>
    <div class="education-grid">
      <article class="education-item">
        <div class="edu-icon">🎓</div>
        <div class="edu-content">
          <h3>Master's Degree in Computer Science</h3>
          <p class="institution">Ecole Supérieure Privée d'Ingénierie et de Technologies (ESPRIT)</p>
          <p class="period">Current</p>
          <p class="description">Full Stack Development • Software Engineering</p>
        </div>
      </article>
      <article class="education-item">
        <div class="edu-icon">📚</div>
        <div class="edu-content">
          <h3>Licence en Sciences de l'Informatique</h3>
          <p class="institution">Faculté des Sciences Mathématiques, Physiques et Naturelles de Tunis</p>
          <p class="period">Bachelor's Degree</p>
          <p class="description">Génie Logiciel • Computer Science</p>
        </div>
      </article>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Education'
}
</script>

<style scoped>
.education {
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

.education-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.25rem;
}

.education-item {
  border: 1px solid var(--line);
  border-radius: 16px;
  padding: 1.5rem;
  transition: var(--transition-medium);
  background: linear-gradient(180deg, rgba(20, 33, 61, 0.5), rgba(11, 19, 40, 0.7));
  display: flex;
  gap: 1rem;
  position: relative;
  overflow: hidden;
}

.education-item::before {
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

.education-item:hover {
  transform: translateY(-6px);
  box-shadow: var(--glow-strong), 0 15px 35px rgba(0, 0, 0, 0.35);
  border-color: var(--orange);
}

.education-item:hover::before {
  opacity: 1;
}

.edu-icon {
  font-size: 2rem;
  flex-shrink: 0;
}

.edu-content h3 {
  margin: 0 0 0.5rem;
  color: var(--orange);
  font-size: 1.1rem;
}

.institution {
  margin: 0 0 0.25rem;
  color: var(--white);
  font-weight: 500;
}

.period {
  margin: 0 0 0.5rem;
  color: var(--text-soft);
  font-size: 0.9rem;
  display: inline-block;
  padding: 0.2rem 0.6rem;
  background: rgba(252, 163, 17, 0.1);
  border-radius: 6px;
}

.description {
  margin: 0;
  color: var(--text-soft);
  font-size: 0.95rem;
}

@media (max-width: 640px) {
  .education-grid {
    grid-template-columns: 1fr;
  }

  .education-item {
    flex-direction: column;
    text-align: center;
  }

  .edu-icon {
    align-self: center;
  }
}
</style>