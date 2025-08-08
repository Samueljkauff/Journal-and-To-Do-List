<template>
  <GuestLayout>
    <Head title="Confirm Password" />
    <p class="py-2 text-center text-white text-2xl font-bold">Confirm Password</p>
    <hr class="border-gray-700"/>
    <div class="px-8 py-4">
      <p class="mb-4 text-sm text-gray-500">
        This is a secure area of the application. Please confirm your password before continuing.
      </p>
      
      <form @submit.prevent="submit">
        <div>
          <label class="block font-medium text-sm text-gray-300">Password</label>
          <input
            id="password"
            type="password"
            class="mt-1 block w-full rounded-md"
            v-model="form.password"
            required
            autocomplete="current-password"
            autofocus
          />
          <p class="text-sm mt-2 text-red-600">{{ form.errors.password }}</p>
        </div>

        <div class="mt-4 flex justify-end">
          <button
            class="px-4 py-2 bg-green-500 rounded-md hover:bg-green-400 text-white font-medium"
            :class="{ 'opacity-25': form.processing }"
            :disabled="form.processing"
          >
            Confirm
          </button>
        </div>
      </form>
    </div>
  </GuestLayout>
</template>

<script lang="ts">
import GuestLayout from '@/Layouts/GuestLayout.vue';
import { Head, useForm } from '@inertiajs/vue3';

export default {
  name: 'ConfirmPassword',
  components: {
    GuestLayout,
    Head
  },
  data() {
    return {
      form: useForm({
        password: '',
      })
    };
  },
  methods: {
    submit() {
      this.form.post(route('password.confirm'), {
        onFinish: () => {
          this.form.reset();
        },
      });
    }
  }
};
</script>