<template>
  <form @submit.prevent="register">
    <div class="lg:w-1/3 mx-auto">
      <div class="mb-4">
        <label for="email" class="label">Your Name</label>
        <input v-model="form.name" type="text" id="name" class="input" />
        <div class="input-error" v-if="form.errors.name">{{ form.errors.name }}
        </div>
      </div>
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
      </div>
      <div class="mb-4">
        <label for="password_confirmation" class="label">Password
          Confirmation</label>
        <input v-model="form.password_confirmation" type="password"
          id="password_confirmation" class="input" />
        <div class="input-error" v-if="form.errors.password_confirmation">{{
          form.errors.password_confirmation
        }}</div>
      </div>
      <div>
        <button type="submit" class="btn-primary w-full mb-4">Create
          Account</button>
        <div class="text-center">
          <Link :href="route('login')" class="text-sm text-gray-500">Already have
          an account? Click here</Link>
        </div>
      </div>
    </div>
  </form>
</template>
<script setup>
import { useForm, Link } from "@inertiajs/vue3";

const form = useForm({
  name: null,
  email: null,
  password: null,
  password_confirmation: null,
});

const register = () => form.post(route('user-account.store'));

</script>
