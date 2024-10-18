<template>
  <nav>
    <ul>
      <li><NuxtLink to="/">Ana Sayfa</NuxtLink></li>
      <li><NuxtLink to="/about">Hakkımızda</NuxtLink></li>
      <li><NuxtLink to="/contact">İletişim</NuxtLink></li>
      <li><NuxtLink to="/admin">Yönetim</NuxtLink></li>
    </ul>
  </nav>
</template>

<script setup>
// Navbar logic can be added here if needed
</script>

<style scoped>
nav {
  background-color: var(--primary-green);
  padding: 1rem;
}

nav ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
  display: flex;
  justify-content: space-around;
}

nav ul li {
  display: inline;
}

a {
  color: var(--white);
  text-decoration: none;
  font-weight: bold;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  transition: background-color 0.3s ease;
}

a:hover {
  background-color: var(--dark-green);
}

.nuxt-link-exact-active {
  background-color: var(--dark-green);
}
</style>