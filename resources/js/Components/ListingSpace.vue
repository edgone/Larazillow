<template>
  <div>
    <span class="font-bold">{{ listing.beds }}</span> bds
    <span class="text-gray-600">| </span>
    <span class="font-bold">{{ listing.baths }}</span> ba
    <span class="text-gray-600">| </span>
    <span class="font-bold">{{ listing.area }}</span> m²
  </div>
</template>
<script setup>
defineProps({ listing: Object });
</script>