<template>
  <form @submit.prevent="login">
    <div class="lg:w-1/3 mx-auto">
      <div class="mb-4">
        <label for="email" class="label">E-mail (username)</label>
        <input v-model="form.email" type="text" id="email" class="input" />
        <div class="input-error" v-if="form.errors.email">{{ form.errors.email }}
        </div>
      </div>
      <div class="mb-4">
        <label for="password" class="label">Password</label>
        <input v-model="form.password" type="password" id="password"
          class="input" />
        <div class="input-error" v-if="form.errors.password">{{
          form.errors.password
        }}</div>
      </div>
      <div>
        <button type="submit" class="btn-primary w-full mb-4">Login</button>

        <div class="text-center">
          <Link :href="route('user-account.create')"
            class="text-sm text-gray-500">Need an account? Click here</Link>
        </div>
      </div>
    </div>
  </form>
</template>

<script setup>
import { useForm, Link } from "@inertiajs/vue3";

const form = useForm({
  email: null,
  password: null,
});

const login = () => form.post(route("login.store"));

</script>
