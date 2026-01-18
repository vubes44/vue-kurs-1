<template>
  <div class="display">
    <p class="display__point">
      Profil: <strong>{{ isPublicProfile ? 'publiczny' : 'prywatny' }}</strong>
    </p>
    <p class="display__point">
      Wiadomości: <strong>{{ formatPermission(whoCanWrite) }}</strong>
    </p>
  </div>
</template>

<script setup>
const props = defineProps({
  isPublicProfile: Boolean,
  whoCanWrite: String,
})

const formatPermission = (val) => {
  switch (val) {
    case 'everyone':
      return 'wszyscy'
    case 'friends':
      return 'tylko znajomi'
    case 'nobody':
      return 'nikt'
    default:
      return val
  }
}
</script>
<style scoped>
.display {
  border: 1px solid #ccc;
  padding: 1rem;
  border-radius: 5px;
  max-width: 300px;
}
.display__point {
  font-family: 'Calibri', sans-serif;
  font-size: 1.1rem;
  margin: 0.5rem 0;
}
</style>
