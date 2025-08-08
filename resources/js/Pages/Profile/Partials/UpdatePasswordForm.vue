<template>
  <section>
    <p class="py-2 text-center text-white text-2xl font-bold">Update Password</p>
    <hr class="border-gray-700"/>
    <div class="px-8 py-4">
      <p class="mb-4 text-sm text-gray-500">
        Ensure your account is using a long, random password to stay secure.
      </p>
      
      <form @submit.prevent="updatePassword">
        <div>
          <label class="block font-medium text-sm text-gray-300">Current Password</label>
          <input
            id="current_password"
            ref="currentPasswordInput"
            type="password"
            class="mt-1 block w-full rounded-md"
            v-model="form.current_password"
            autocomplete="current-password"
          />
          <p class="text-sm mt-2 text-red-600">{{ form.errors.current_password }}</p>
        </div>

        <div class="mt-4">
          <label class="block font-medium text-sm text-gray-300">New Password</label>
          <input
            id="password"
            ref="passwordInput"
            type="password"
            class="mt-1 block w-full rounded-md"
            v-model="form.password"
            autocomplete="new-password"
          />
          <p class="text-sm mt-2 text-red-600">{{ form.errors.password }}</p>
        </div>

        <div class="mt-4">
          <label class="block font-medium text-sm text-gray-300">Confirm Password</label>
          <input
            id="password_confirmation"
            type="password"
            class="mt-1 block w-full rounded-md"
            v-model="form.password_confirmation"
            autocomplete="new-password"
          />
          <p class="text-sm mt-2 text-red-600">{{ form.errors.password_confirmation }}</p>
        </div>

        <div class="mt-4 flex items-center justify-between">
          <div class="flex items-center">
            <span
              v-if="form.recentlySuccessful"
              class="text-sm text-green-400 transition ease-in-out"
            >
              Saved.
            </span>
          </div>
          <button
            class="px-4 py-2 bg-green-500 rounded-md hover:bg-green-400 font-medium"
            :class="{ 'opacity-25': form.processing }"
            :disabled="form.processing"
          >
            Save
          </button>
        </div>
      </form>
    </div>
  </section>
</template>

<script lang="ts">
import { useForm } from '@inertiajs/vue3';

export default {
  name: 'UpdatePassword',
  data() {
    return {
      form: useForm({
        current_password: '',
        password: '',
        password_confirmation: '',
      })
    };
  },
  methods: {
    updatePassword() {
      this.form.put(route('password.update'), {
        preserveScroll: true,
        onSuccess: () => {
          this.form.reset();
        },
        onError: () => {
          if (this.form.errors.password) {
            this.form.reset('password', 'password_confirmation');
            (this.$refs.passwordInput as HTMLInputElement)?.focus();
          }
          if (this.form.errors.current_password) {
            this.form.reset('current_password');
            (this.$refs.currentPasswordInput as HTMLInputElement)?.focus();
          }
        },
      });
    }
  }
};
</script>