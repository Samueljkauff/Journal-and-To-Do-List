<template>
  <section>
    <p class="py-2 text-center text-white text-2xl font-bold">Delete Account</p>
    <hr class="border-gray-700"/>
    <div class="px-8 py-4">
      <p class="mb-4 text-sm text-gray-500">
        Once your account is deleted, all of its resources and data will be permanently deleted. Before deleting your account, please download any data or information that you wish to retain.
      </p>
      
      <button
        @click="confirmUserDeletion"
        class="px-4 py-2 bg-red-600 rounded-md hover:bg-red-500 text-white font-medium"
      >
        Delete Account
      </button>

      <!-- Modal -->
      <div v-if="confirmingUserDeletion" class="fixed inset-0 z-50 flex items-center justify-center bg-black bg-opacity-50">
        <div class="border bg-gray-800 border-gray-700 rounded-lg shadow-lg max-w-md w-full mx-4">
          <div class="p-6">
            <h2 class="text-lg font-medium text-white">
              Are you sure you want to delete your account?
            </h2>
            
            <p class="mt-1 text-sm text-gray-500">
              Once your account is deleted, all of its resources and data will be permanently deleted. Please enter your password to confirm you would like to permanently delete your account.
            </p>

            <div class="mt-6">
              <label class="sr-only">Password</label>
              <input
                id="password"
                ref="passwordInput"
                type="password"
                class="mt-1 block w-3/4 rounded-md border-gray-300 shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50"
                placeholder="Password"
                v-model="form.password"
                @keyup.enter="deleteUser"
              />
              <p class="text-sm mt-2 text-red-600">{{ form.errors.password }}</p>
            </div>

            <div class="mt-6 flex justify-end space-x-3">
              <button
                @click="closeModal"
                class="px-4 py-2 bg-gray-300 rounded-md hover:bg-gray-400 text-gray-700 font-medium"
              >
                Cancel
              </button>
              
              <button
                @click="deleteUser"
                class="px-4 py-2 bg-red-600 rounded-md hover:bg-red-500 font-medium"
                :class="{ 'opacity-25': form.processing }"
                :disabled="form.processing"
              >
                Delete Account
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { useForm } from '@inertiajs/vue3';

export default {
  name: 'DeleteAccount',
  data() {
    return {
      confirmingUserDeletion: false,
      form: useForm({
        password: '',
      })
    };
  },
  methods: {
    confirmUserDeletion() {
      this.confirmingUserDeletion = true;
      this.$nextTick(() => {
        (this.$refs.passwordInput as HTMLInputElement)?.focus();
      });
    },
    
    deleteUser() {
      this.form.delete(route('profile.destroy'), {
        preserveScroll: true,
        onSuccess: () => this.closeModal(),
        onError: () => (this.$refs.passwordInput as HTMLInputElement)?.focus(),
        onFinish: () => {
          this.form.reset();
        },
      });
    },
    
    closeModal() {
      this.confirmingUserDeletion = false;
      this.form.clearErrors();
      this.form.reset();
    }
  }
};
</script>