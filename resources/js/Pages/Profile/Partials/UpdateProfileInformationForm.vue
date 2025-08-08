<template>
  <section>
    <p class="py-2 text-center text-white text-2xl font-bold">Profile Information</p>
    <hr class="border-gray-700"/>
    <div class="px-8 py-4">
      <p class="mb-4 text-sm text-gray-500">
        Update your account's profile information and email address.
      </p>
      
      <form @submit.prevent="submit">
        <div>
          <label class="block font-medium text-sm text-gray-300">Name</label>
          <input
            id="name"
            type="text"
            class="mt-1 block w-full rounded-md"
            v-model="form.name"
            required
            autofocus
            autocomplete="name"
          />
          <p class="text-sm mt-2 text-red-600">{{ form.errors.name }}</p>
        </div>

        <div class="mt-4">
          <label class="block font-medium text-sm text-gray-300">Email</label>
          <input
            id="email"
            type="email"
            class="mt-1 block w-full rounded-md"
            v-model="form.email"
            required
            autocomplete="username"
          />
          <p class="text-sm mt-2 text-red-600">{{ form.errors.email }}</p>
        </div>

        <div v-if="mustVerifyEmail && user.email_verified_at === null" class="mt-4">
          <p class="text-sm text-gray-500">
            Your email address is unverified.
            <Link
              :href="route('verification.send')"
              method="post"
              as="button"
              class="text-sm text-gray-400 underline hover:text-gray-300 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
            >
              Click here to re-send the verification email.
            </Link>
          </p>
          <div
            v-show="status === 'verification-link-sent'"
            class="mt-2 text-sm font-medium text-green-400"
          >
            A new verification link has been sent to your email address.
          </div>
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
import { Link, useForm, usePage } from '@inertiajs/vue3';

export default {
  name: 'ProfileInformation',
  components: {
    Link
  },
  props: {
    mustVerifyEmail: {
      type: Boolean,
      default: false
    },
    status: {
      type: String,
      default: undefined
    }
  },
  data() {
    const user = usePage().props.auth.user;
    return {
      user,
      form: useForm({
        name: user.name,
        email: user.email,
      })
    };
  },
  methods: {
    submit() {
      this.form.patch(route('profile.update'));
    }
  }
};
</script>