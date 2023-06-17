<template>
  <span>
    {{ listing.city }} {{ listing.street_nr }}, {{ listing.city }}
  </span>
</template>
<script setup>
defineProps({ listing: Object });
</script>