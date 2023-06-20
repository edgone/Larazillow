<template>
  <Box>
    <div class="mb-2">
      <Link :href="route('listing.show', { listing: listing.id })">
      <div class="flex items-center gap-1">
        <Price :price="listing.price" class="text-2xl font-bold" />
        <div class="text-xs text-gray-500">
          <Price :price="monthlyPayment" /> pm
        </div>
      </div>
      <ListingSpace :listing="listing" class="text-lg" />
      <ListingAddress :listing="listing" class="text-gray-400" />
      </Link>
    </div>
    <div class="flex gap-4">
      <div>
        <Link :href="route('listing.edit', { listing: listing.id })"
          class="text-indigo-300">Edit
        </Link>
      </div>
      <div>
        <Link :href="route('listing.destroy', { listing: listing.id })"
          method="delete" as="button" class="text-red-300">
        Delete
        </Link>
      </div>
    </div>
  </Box>
</template>

<script setup>
import { Link } from '@inertiajs/vue3';
import Price from '@/Components/UI/Price.vue'
import ListingSpace from '@/Components/ListingSpace.vue'
import Box from '@/Components/UI/Box.vue'
import ListingAddress from '@/Components/ListingAddress.vue';
import { useMonthlyPayment } from '@/Composables/useMonthlyPayment';

const props = defineProps({ listing: Object });
const { monthlyPayment } = useMonthlyPayment(props.listing.price, 2.5, 25);

</script>
