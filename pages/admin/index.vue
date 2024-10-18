<template>
  <div>
    <h1>Yönetim Paneli</h1>
    <div v-if="!isAuthenticated">
      <h2>Giriş</h2>
      <input v-model="password" type="password" placeholder="Şifre girin" />
      <button @click="login">Giriş Yap</button>
    </div>
    <div v-else>
      <button @click="logout">Çıkış Yap</button>
      <h2>Sayfa Yönetimi</h2>
      <PageList :pages="pages" @edit="editPage" @delete="deletePage" />
      <PageForm :pageToEdit="pageToEdit" @add="addPage" @update="updatePage" />
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const isAuthenticated = ref(false)
const password = ref('')
const pageToEdit = ref(null)

const pages = reactive([
  { id: 1, title: 'Ana Sayfa', content: 'Ana sayfamıza hoş geldiniz' },
  { id: 2, title: 'Hakkımızda', content: 'Şirketimiz hakkında bilgi edinin' },
  { id: 3, title: 'İletişim', content: 'Bizimle iletişime geçin' }
])

const login = () => {
  if (password.value === 'admin') {
    isAuthenticated.value = true
  } else {
    alert('Geçersiz şifre')
  }
}

const logout = () => {
  isAuthenticated.value = false
  password.value = ''
}

const addPage = (newPage) => {
  pages.push({ id: pages.length + 1, ...newPage })
}

const editPage = (page) => {
  pageToEdit.value = page
}

const updatePage = (updatedPage) => {
  const index = pages.findIndex(p => p.id === updatedPage.id)
  if (index !== -1) {
    pages[index] = updatedPage
  }
  pageToEdit.value = null
}

const deletePage = (pageId) => {
  const index = pages.findIndex(p => p.id === pageId)
  if (index !== -1) {
    pages.splice(index, 1)
  }
}
</script>