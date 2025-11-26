<script setup>
import { Head, Link, useForm } from '@inertiajs/vue3';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';

const form = useForm({
    email: '',
    password: '',
    remember: false, 
});

const submit = () => {
    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>

<template>
    <Head title="Log in" />

    <div class="min-h-screen bg-black flex items-center justify-center py-12 px-4 sm:px-6 lg:px-8">
        <div class="max-w-md w-full space-y-8">
            <div class="text-center">
                <ApplicationLogo class="mx-auto h-20 w-auto" />
                <h2 class="mt-6 text-4xl font-extrabold text-white">Sign in to your account</h2>
            </div>

            <div class="bg-white rounded-lg shadow-xl p-8">
                <!-- Error messages -->
                <div v-if="form.errors.any()" class="mb-4 p-3 bg-red-50 text-red-700 rounded">
                    <div v-for="error in Object.values(form.errors)" :key="error">{{ error }}</div>
                </div>

                <form @submit.prevent="submit" class="space-y-6">
                    <div>
                        <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
                        <input id="email" v-model="form.email" type="email" required autocomplete="email"
                               class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500" />
                    </div>

                    <div>
                        <label for="password" class="block text-sm font-medium text-gray-700">Password</label>
                        <input id="password" v-model="form.password" type="password" required autocomplete="current-password"
                               class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500" />
                    </div>

                    <div class="flex items-center justify-between">
                        <div class="flex items-center">
                            <input id="remember" v-model="form.remember" type="checkbox" class="h-4 w-4 text-green-600 rounded" />
                            <label for="remember" class="ml-2 text-sm text-gray-900">Remember me</label>
                        </div>
                        <Link :href="route('password.request')" class="text-sm text-green-600 hover:text-green-500">
                            Forgot password?
                        </Link>
                    </div>

                    <button type="submit" :disabled="form.processing"
                            class="w-full py-3 px-4 bg-green-600 hover:bg-green-700 text-white font-medium rounded-md disabled:opacity-50">
                        {{ form.processing ? 'Signing in...' : 'Sign in' }}
                    </button>

                    <div class="text-center text-sm">
                        <Link :href="route('register')" class="text-green-600 hover:text-green-500">
                            Need an account? Register
                        </Link>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>