<script setup lang="ts">
import GuestLayout from '@/Layouts/GuestLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => {
            form.reset('password', 'password_confirmation');
        },
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Register" />
        <p class="py-2 text-center text-white text-2xl font-bold">Register</p>
        <hr class="border-gray-700"/>
        <div class="px-8 py-4">
        <form @submit.prevent="submit">
            <div>
                <label class="block font-medium text-sm text-gray-300">Name</label>


                <input
                    id="name"
                    type="text"
                    class="mt-1 block w-full"
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
                    class="mt-1 block w-full"
                    v-model="form.email"
                    required
                    autocomplete="username"
                />

                <p class="text-sm mt-2 text-red-600">{{ form.errors.email }}</p>
            </div>

            <div class="mt-4">
                <label class="block font-medium text-sm text-gray-300">Password</label>

                <input
                    id="password"
                    type="password"
                    class="mt-1 block w-full"
                    v-model="form.password"
                    required
                    autocomplete="new-password"
                />

                <p class="text-sm mt-2 text-red-600">{{ form.errors.password }}</p>
            </div>

            <div class="mt-4">
                <label class="block font-medium text-sm text-gray-300">
                    Confirm Password
                </label>

                <input
                    id="password_confirmation"
                    type="password"
                    class="mt-1 block w-full"
                    v-model="form.password_confirmation"
                    required
                    autocomplete="new-password"
                />

                <p class="text-sm mt-2 text-red-600">{{ form.errors.password_confirmation }}</p>
            </div>

            <div class="mt-4 flex items-center justify-between">
                <Link
                    :href="route('login')"
                    class="rounded-md text-sm text-gray-600 underline hover:text-gray-900 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
                >
                    Already registered?
                </Link>

                <button
                    class="ms-1 px-2 bg-green-500 rounded-md h-8 hover:bg-green-400"
                    :class="{ 'opacity-25': form.processing }"
                    :disabled="form.processing"
                >
                    Register
            </button>
            </div>
        </form>
        </div>
    </GuestLayout>
</template>
