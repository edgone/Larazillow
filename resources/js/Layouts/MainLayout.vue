<template>
    <header class="border-b-2 border-gray-200 dark:border-gray-700 bg-white dark:bg-gray-800 w-full shadow-lg mb-4">
        <div class="container mx-auto">
            <nav class="p-4 flex items-center justify-between">
                <div class="flex items-center text-lg gap-2">
                    <Link
                        :href="route('listing.index')"
                        class="dark:text-indigo-100 dark:hover:text-indigo-200 text-indigo-800 hover:text-indigo-900 py-2 pr-6 rounded-md font-medium"
                    >
                        Listings
                    </Link>
                    <div v-if="user">
                        <Link
                            :href="
                                route('realtor.listing.edit', {
                                    listing: page.props.listing.id,
                                })
                            "
                            class="dark:text-indigo-200 dark:hover:bg-indigo-200 dark:hover:text-indigo-800 py-2 px-6 rounded-md font-medium"
                            v-if="page.component === 'Listing/Show'"
                            >Edit</Link
                        >
                    </div>
                </div>
                <div class="text-xl text-indigo-600 dark:text-indigo-300 font-bold">
                    <Link :href="route('listing.index')"> Larazillow </Link>
                </div>
                <div class="flex items-center gap-4" v-if="user">
                    <Link :href="route('notification.index')" class="text-gray-500 relative pr-2 py-2 text-lg">
                        🔔
                        <div
                            v-if="notificationCount"
                            class="absolute right-0 top-0 w-5 -h-5 bg-red-700 dark:bg-red-400 text-white font-medium border border-white dark:border-gray-900 rounded-full text-sm text-center"
                        >
                            {{ notificationCount }}
                        </div>
                    </Link>
                    <Link :href="route('realtor.listing.index')" class="text-sm text-gray-500 dark:text-gray-200">{{ user.name }} </Link>
                    <Link :href="route('realtor.listing.create')" class="btn-primary"> + New Listing</Link>
                    <div>
                        <Link :href="route('logout')" method="delete" as="button">Logout </Link>
                    </div>
                </div>
                <div v-else class="flex items-center gap-4">
                    <Link :href="route('user-account.create')" class="btn-primary">Register </Link>
                    <Link :href="route('login')">Sign-in</Link>
                </div>
            </nav>
        </div>
    </header>
    <main class="container mx-auto p-4 w-full">
        <div
            v-if="flashSuccess"
            class="mb-4 border rounded-md shadow-sm text-gray-100 dark:text-gray-100 border-green-200 dark:border-green-800 bg-green-500 dark:bg-green-700 py-2 px-4"
        >
            {{ flashSuccess }}
        </div>
        <slot />
    </main>
</template>

<script setup>
import { computed } from "vue";
import { Link, usePage } from "@inertiajs/vue3";

const page = usePage();

const flashSuccess = computed(() => page.props.flash.success);

const user = computed(() => page.props.user);

const notificationCount = computed(() => Math.min(user.value.notificationCount, 9));
</script>
