<template>
  <div class="privacy-settings">
    <Header title="Ustawienia prywatności" />

    <section>
      <h3 class="section__header">Widoczność profilu</h3>
      <PublicProfileToggle v-model="isPublic" />
    </section>

    <section>
      <h3 class="section__header">Kto może pisać</h3>
      <MessagePermissionPicker
        :value="messagePermission"
        :disabled="!isPublic"
        @change="messagePermission = $event"
      />
      <p v-if="!isPublic" class="section__warning">
        profil prywatny i nie można wysyłać wiadomosci
      </p>
    </section>

    <section>
      <h3 class="section__header">Podgląd</h3>
      <Display :is-public-profile="isPublic" :who-can-write="messagePermission" />
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import PublicProfileToggle from './PublicProfileToggle.vue'
import MessagePermissionPicker from './MessagePermissionPicker.vue'
import Display from './Display.vue'
import Header from './Header.vue'

const isPublic = ref(true)
const messagePermission = ref('everyone')
</script>

<style scoped>
.privacy-settings {
  max-width: 600px;
  margin: 2rem auto;
  padding: 1rem;
}

.section__header {
  font-family: 'Calibri', sans-serif;
  font-size: 1.25rem;
  margin-bottom: 1rem;
}

section {
  margin: 2rem 0;
}

.section__warning {
  color: #494949;
  font-size: 0.9rem;
  margin-top: 0.5rem;
}
</style>
