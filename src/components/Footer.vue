<template>
  <footer class="main-footer">
    <p>© {{ currentYear }} Fares Ben Ali — Full Stack Developer ⚡</p>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  data() {
    return {
      currentYear: new Date().getFullYear()
    };
  }
}
</script>

<style scoped>
.main-footer {
  margin-top: 2rem;
  padding: 1.25rem;
  text-align: center;
  color: var(--alabaster-grey);
  background: color-mix(in srgb, var(--panel-strong) 88%, var(--black));
  border-top: 1px solid var(--line);
  box-shadow: 0 -10px 35px rgba(0, 0, 0, 0.35);
}

p {
  margin: 0;
  font-size: 0.95rem;
  letter-spacing: 0.3px;
}
</style>