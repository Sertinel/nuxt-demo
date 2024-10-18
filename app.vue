<template>
  <div id="app">
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>

<style>
@import '@/assets/theme.css';

#app {
  font-family: Arial, sans-serif;
  background-color: var(--off-white);
  color: var(--dark-green);
}

h1, h2, h3, h4, h5, h6 {
  color: var(--primary-green);
}

a {
  color: var(--light-green);
  text-decoration: none;
}

a:hover {
  color: var(--dark-green);
}

.btn {
  background-color: var(--primary-green);
  color: var(--white);
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.btn:hover {
  background-color: var(--dark-green);
}
</style>