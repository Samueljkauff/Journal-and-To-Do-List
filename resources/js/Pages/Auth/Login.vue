<template>
  <GuestLayout>
    <Head title="Log in" />
    <p class="py-2 text-center text-white text-2xl font-bold">Login!</p>
    <hr class="border-gray-700"/>
    <div class="px-8 py-4">
      <form @submit.prevent="submit">
        <div>
          <label class="block font-medium text-sm text-gray-300">Email</label>
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
        <div class="mt-4">
          <label class="block font-medium text-sm text-gray-300">Password</label>
          <input
            id="password"
            type="password"
            class="mt-1 block w-full rounded-md"
            v-model="form.password"
            required
            autocomplete="current-password"
          />
          <p class="text-sm mt-2 text-red-600">{{ form.errors.password }}</p>
        </div>
        <div class="mt-4 flex items-center">
          <input type="checkbox" name="remember" v-model="form.remember" class="rounded border-gray-300 text-green-500 shadow-sm focus:ring-green-400" />
          <span class="ms-2 text-sm text-gray-500">Remember me</span>
        </div>
        <div class="mt-4 flex items-center justify-between">
          <Link
            v-if="canResetPassword"
            :href="route('password.request')"
            class="text-start rounded-md text-sm text-gray-500 underline hover:text-gray-600 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
          >
            Forgot your password?
          </Link>
          <button
            class="ms-1 px-2 bg-green-500 rounded-md h-8 hover:bg-green-400"
            :class="{ 'opacity-25': form.processing }"
            :disabled="form.processing"
          >
            Log in
          </button>
        </div>
      </form>
    </div>
    <hr class="border-gray-700 py-2">
    <Link :href="route('register')" class="text-white flex justify-center mb-2 font-bold hover:underline">Don't have an account?</Link>
  </GuestLayout>
</template>

<script lang="ts">
import GuestLayout from '@/Layouts/GuestLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

export default {
  name: 'Login',
  
  components: {
    GuestLayout,
    Head,
    Link
  },
  
  props: {
    canResetPassword: {
      type: Boolean,
      default: false
    },
    status: {
      type: String,
      default: undefined
    }
  },
  
  data() {
    return {
      form: useForm({
        email: '',
        password: '',
        remember: false,
      })
    };
  },
  
  methods: {
    submit() {
      this.form.post(route('login'), {
        onFinish: () => {
          this.form.reset('password');
        }
      });
    }
  }
};
</script>