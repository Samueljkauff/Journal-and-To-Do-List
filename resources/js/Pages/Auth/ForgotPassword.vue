<template>
  <GuestLayout>
    <Head title="Forgot Password" />
    <div class="mb-4 max-w-96 text-sm text-gray-600 p-2">
      Forgot your password? No problem. Just let us know your email
      address and we will email you a password reset link that will allow
      you to choose a new one.
    </div>
    <form @submit.prevent="submit" class="p-3">
      <div>
        <label class="text-sm text-white">Email</label>
        <input
          id="email"
          type="email"
          class="mt-1 block w-full rounded-md"
          v-model="form.email"
          required
          autofocus
          autocomplete="username"
        />
        <p class="text-sm mt-2 text-red-600">{{ form.errors.email }}</p>
      </div>
      <div class="mt-4 flex items-center justify-between">
        <Link :href="route('login')" class="text-gray-600 underline text-sm hover:text-gray-700">
            Back to Login
        </Link>
        <button
            class="ms-1 px-2 bg-green-500 rounded-md h-8 hover:bg-green-400"
            :class="{ 'opacity-25': form.processing }"
            :disabled="form.processing"
          >
            Email Password Reset Link
          </button>
      </div>
    </form>
  </GuestLayout>
</template>

<script lang="ts">
import GuestLayout from '@/Layouts/GuestLayout.vue';
import { Head, useForm, Link } from '@inertiajs/vue3';

export default {
  name: 'ForgotPassword',
  
  components: {
    GuestLayout,
    Head,
    Link
  },
  
  props: {
    status: {
      type: String,
      default: undefined
    }
  },
  
  data() {
    return {
      form: useForm({
        email: ''
      })
    };
  },
  
  methods: {
    submit() {
      this.form.post(route('password.email'));
    }
  }
};
</script>