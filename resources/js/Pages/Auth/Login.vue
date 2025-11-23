<script setup>
import { Head, Link, useForm } from '@inertiajs/vue3';  
import ApplicationLogo from '@/Components/ApplicationLogo.vue';

const form = useForm({     
    email: '',
    password: '',
    remember: false,
});

const submit = () => {
    form.post(route('login'));
};
</script>

<template>
    <Head title="Log in" />

    <!-- Full black background -->
    <div class="min-h-screen bg-black flex items-center justify-center py-12 px-4 sm:px-6 lg:px-8">
        <div class="max-w-md w-full space-y-8">
            <!-- Big green logo centered -->
            <div class="text-center">
                <ApplicationLogo class="mx-auto h-20 w-auto" />
                <h2 class="mt-6 text-center text-3xl font-extrabold text-white">
                    Sign in to your account
                </h2>
            </div>

            <!-- White form card -->
            <div class="bg-white rounded-lg shadow-xl p-8">
                <form @submit.prevent="submit" class="space-y-6">
                    <div>
                        <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
                        <input
                            id="email"
                            v-model="form.email"
                            type="email"
                            required
                            class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500"
                        />
                    </div>

                    <div>
                        <label for="password" class="block text-sm font-medium text-gray-700">Password</label>
                        <input
                            id="password"
                            v-model="form.password"
                            type="password"
                            required
                            class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500"
                        />
                    </div>

                    <div class="flex items-center justify-between">
                        <div class="flex items-center">
                            <input id="remember" v-model="form.remember" type="checkbox" class="h-4 w-4 text-green-600 focus:ring-green-500 border-gray-300 rounded" />
                            <label for="remember" class="ml-2 block text-sm text-gray-900">Remember me</label>
                        </div>

                        <div v-if="canResetPassword" class="text-sm">
                            <Link :href="route('password.request')" class="font-medium text-green-600 hover:text-green-500">
                                Forgot your password?
                            </Link>
                        </div>
                    </div>

                    <div v-if="form.errors.any()" class="mb-4 text-sm text-red-600">
                        <div v-for="error in form.errors">{{ error }}</div>
                    </div>

                    <div>
                        <button type="submit"
                            class="w-full flex justify-center py-3 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-green-600 hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500">
                            Sign in
                        </button>
                    </div>

                    <div class="text-center text-sm">
                        <Link :href="route('register')" class="font-medium text-green-600 hover:text-green-500">
                            Need an account? Sign up
                        </Link>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>