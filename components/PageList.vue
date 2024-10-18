<template>
  <div class="page-list">
    <h3>Mevcut Sayfalar</h3>
    <ul>
      <li v-for="page in pages" :key="page.id">
        <span class="page-title">{{ page.title }}</span>
        <div class="button-group">
          <button class="btn edit" @click="$emit('edit', page)">Düzenle</button>
          <button class="btn delete" @click="$emit('delete', page.id)">Sil</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script setup>
defineProps(['pages'])
defineEmits(['edit', 'delete'])
</script>

<style scoped>
.page-list {
  background-color: var(--white);
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

h3 {
  color: var(--primary-green);
  margin-bottom: 15px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
  border-bottom: 1px solid var(--light-green);
}

li:last-child {
  border-bottom: none;
}

.page-title {
  color: var(--dark-green);
  font-weight: bold;
}

.button-group {
  display: flex;
  gap: 10px;
}

.btn {
  padding: 5px 10px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
  transition: background-color 0.3s ease;
}

.btn.edit {
  background-color: var(--light-green);
  color: var(--white);
}

.btn.delete {
  background-color: #f44336;
  color: var(--white);
}

.btn:hover {
  opacity: 0.8;
}
</style>