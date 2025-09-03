<template>
    <Head title="Profile" />

    <PageLayout>
        <div class="w-full flex flex-col justify-center items-center m-4 p-8 bg-gray-900 rounded-xl">
            <div class="flex flex-row m-4">
                <div
                    class="p-8 m-4 h-full border bg-gray-800 border-gray-700 rounded-lg flex flex-col"
                >
                    <UpdateProfileInformationForm
                        :must-verify-email="mustVerifyEmail"
                        class="max-w-xl"
                    />
                </div>

                <div
                    class="p-8 m-4 h-full border bg-gray-800 border-gray-700 rounded-lg flex flex-col"
                >
                    <UpdatePasswordForm />
                </div>
            </div>
                <div
                    class="p-8 m-8 border bg-gray-800 border-gray-700 rounded-lg flex flex-col"
                >
                    <DeleteUserForm class="max-w-xl" />
                </div>
            </div>
    </PageLayout>
</template>

<script setup lang="ts">
import DeleteUserForm from './Partials/DeleteUserForm.vue';
import UpdatePasswordForm from './Partials/UpdatePasswordForm.vue';
import UpdateProfileInformationForm from './Partials/UpdateProfileInformationForm.vue';
import { Head } from '@inertiajs/vue3';
import PageLayout from '@/Components/PageLayout.vue';

defineProps<{
    mustVerifyEmail?: boolean;
    status?: string;
}>();
</script>
