<template>
  <div class="page-form">
    <h3>{{ isEditing ? 'Sayfayı Düzenle' : 'Yeni Sayfa Ekle' }}</h3>
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <input v-model="form.title" placeholder="Sayfa Başlığı" required />
      </div>
      <div class="form-group">
        <textarea v-model="form.content" placeholder="Sayfa İçeriği" required></textarea>
      </div>
      <div class="button-group">
        <button type="submit" class="btn submit">{{ isEditing ? 'Güncelle' : 'Ekle' }}</button>
        <button v-if="isEditing" type="button" @click="cancelEdit" class="btn cancel">İptal</button>
      </div>
    </form>
  </div>
</template>

<script setup>
import { ref, reactive, watch } from 'vue'

const props = defineProps({
  pageToEdit: { type: Object, default: null }
})

const emit = defineEmits(['add', 'update'])

const isEditing = ref(false)
const form = reactive({
  title: '',
  content: ''
})

const resetForm = () => {
  form.title = ''
  form.content = ''
  isEditing.value = false
}

const submitForm = () => {
  if (isEditing.value) {
    emit('update', { ...props.pageToEdit, ...form })
  } else {
    emit('add', { ...form })
  }
  resetForm()
}

const cancelEdit = () => {
  resetForm()
  emit('update', null)
}

watch(() => props.pageToEdit, (newVal) => {
  if (newVal) {
    form.title = newVal.title
    form.content = newVal.content
    isEditing.value = true
  } else {
    resetForm()
  }
}, { immediate: true })
</script>

<style scoped>
.page-form {
  background-color: var(--white);
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

h3 {
  color: var(--primary-green);
  margin-bottom: 15px;
}

.form-group {
  margin-bottom: 15px;
}

input, textarea {
  width: 100%;
  padding: 10px;
  border: 1px solid var(--light-green);
  border-radius: 4px;
  font-size: 16px;
}

textarea {
  min-height: 100px;
  resize: vertical;
}

.button-group {
  display: flex;
  gap: 10px;
}

.btn {
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
  transition: background-color 0.3s ease;
}

.btn.submit {
  background-color: var(--primary-green);
  color: var(--white);
}

.btn.cancel {
  background-color: #f44336;
  color: var(--white);
}

.btn:hover {
  opacity: 0.8;
}
</style>