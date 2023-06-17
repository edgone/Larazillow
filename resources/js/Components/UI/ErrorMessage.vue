<template>
  <span class="input-error">{{ error }}</span>
</template>
<script setup>
defineProps({ error: String });
</script>