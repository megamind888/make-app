<script setup>
import { Head, Link, useForm } from '@inertiajs/vue3';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>

<template>
    <Head title="Register" />

    <div class="min-h-screen bg-black flex items-center justify-center py-12 px-4 sm:px-6 lg:px-8">
        <div class="max-w-md w-full space-y-8">
            <div class="text-center">
                <ApplicationLogo class="mx-auto h-20 w-auto" />
                <h2 class="mt-6 text-4xl font-extrabold text-white">Create your account</h2>
                <p class="mt-2 text-sm text-gray-300">Join the maker revolution</p>
            </div>

            <div class="bg-white rounded-lg shadow-xl p-8">
                <div v-if="form.errors.any()" class="mb-4 p-3 bg-red-50 text-red-700 rounded">
                    <div v-for="error in Object.values(form.errors)" :key="error">{{ error }}</div>
                </div>

                <form @submit.prevent="submit" class="space-y-6">
                    <div>
                        <label for="name" class="block text-sm font-medium text-gray-700">Name</label>
                        <input id="name" v-model="form.name" type="text" required
                               class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500" />
                    </div>

                    <div>
                        <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
                        <input id="email" v-model="form.email" type="email" required
                               class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500" />
                    </div>

                    <div>
                        <label for="password" class="block text-sm font-medium text-gray-700">Password</label>
                        <input id="password" v-model="form.password" type="password" required
                               class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500" />
                    </div>

                    <div>
                        <label for="password_confirmation" class="block text-sm font-medium text-gray-700">Confirm Password</label>
                        <input id="password_confirmation" v-model="form.password_confirmation" type="password" required
                               class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500" />
                    </div>

                    <button type="submit" :disabled="form.processing"
                            class="w-full py-3 px-4 bg-green-600 hover:bg-green-700 text-white font-medium rounded-md disabled:opacity-50">
                        {{ form.processing ? 'Creating...' : 'Register' }}
                    </button>

                    <div class="text-center text-sm">
                        <Link :href="route('login')" class="text-green-600 hover:text-green-500">
                            Already registered? Sign in
                        </Link>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>