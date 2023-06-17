<template>
  <header
    class="border-b-2 border-gray-200 dark:border-gray-700 bg-white dark:bg-gray-800 w-full shadow-lg">
    <div class="container mx-auto">
      <nav class="p-4 flex items-center justify-between">
        <div class="text-lg space-x-4">
          <Link :href="route('listing.index')"
            class="dark:text-indigo-100 dark:hover:text-indigo-200 text-indigo-800 hover:text-indigo-900 py-2 px-6 rounded-md font-medium">
          Listings
          </Link>

          <Link :href="route('listing.edit', { listing: page.props.listing.id })"
            class="dark:text-indigo-200 dark:hover:bg-indigo-200 dark:hover:text-indigo-800 py-2 px-6 rounded-md font-medium"
            v-if="page.component === 'Listing/Show'">Edit</Link>
        </div>
        <div class="text-xl text-indigo-600 dark:text-indigo-300 font-bold">
          <Link :href="route('listing.index')">
          Larazillow
          </Link>
        </div>
        <div>
          <Link :href="route('listing.create')" class="btn-primary">
          +
          New
          Listing</Link>
        </div>
      </nav>
    </div>
  </header>
  <main class="container mx-auto p-4">
    <div v-if="flashSuccess"
      class="mb-4 border rounded-md shadow-sm border-green-200 dark:border-green-900 bg-green-500 dark:bg-green-900 p-4">
      {{ flashSuccess }}
    </div>
    <slot />
  </main>
</template>

<script setup>
import { computed } from 'vue';
import { Link, usePage } from '@inertiajs/vue3'

const page = usePage();

const flashSuccess = computed(() => page.props.flash.success);

</script>