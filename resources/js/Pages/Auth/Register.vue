<script setup>
import { Head, Link } from '@inertiajs/vue3';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('register'));
};
</script>

<template>
    <Head title="Register" />

    <!-- Black background + centered everything -->
    <div class="min-h-screen bg-black flex items-center justify-center py-12 px-4 sm:px-6 lg:px-8">
        <div class="max-w-md w-full space-y-8">
            <!-- Green logo + heading -->
            <div class="text-center">
                <ApplicationLogo class="mx-auto h-20 w-auto" />
                <h2 class="mt-6 text-4xl font-extrabold text-white">Create your account</h2>
                <p class="mt-2 text-sm text-gray-300">Join the maker revolution</p>
            </div>

            <!-- White form card -->
            <div class="bg-white rounded-lg shadow-xl p-8">
                <form @submit.prevent="submit" class="space-y-6">
                    <div>
                        <label for="name" class="block text-sm font-medium text-gray-700">Name</label>
                        <input id="name" v-model="form.name" type="text" required autocomplete="name"
                               class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500" />
                    </div>

                    <div>
                        <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
                        <input id="email" v-model="form.email" type="email" required autocomplete="username"
                               class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500" />
                    </div>

                    <div>
                        <label for="password" class="block text-sm font-medium text-gray-700">Password</label>
                        <input id="password" v-model="form.password" type="password" required autocomplete="new-password"
                               class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500" />
                    </div>

                    <div>
                        <label for="password_confirmation" class="block text-sm font-medium text-gray-700">Confirm Password</label>
                        <input id="password_confirmation" v-model="form.password_confirmation" type="password" required autocomplete="new-password"
                               class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500" />
                    </div>
                    
                    <div v-if="form.errors.any()" class="mb-4 text-sm text-red-600">
                        <div v-for="error in form.errors">{{ error }}</div>
                    </div>

                    <div>
                        <button type="submit"
                                class="w-full flex justify-center py-3 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-green-600 hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500">
                            Register
                        </button>
                    </div>

                    <div class="text-center text-sm">
                        <Link :href="route('login')" class="font-medium text-green-600 hover:text-green-500">
                            Already have an account? Sign in
                        </Link>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>