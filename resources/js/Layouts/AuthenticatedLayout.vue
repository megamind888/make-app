<script setup>
import { Link } from '@inertiajs/vue3';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
</script>

<template>
    <div class="min-h-screen bg-gray-50 flex">
        <!-- Sidebar -->
        <aside class="w-64 bg-white shadow-md">
            <div class="p-6 border-b">
                <ApplicationLogo />
            </div>
            <nav class="mt-6">
                <Link :href="route('dashboard')" class="flex items-center px-6 py-3 text-gray-700 hover:bg-green-50 border-l-4 border-transparent hover:border-green-500">
                    <span class="ml-3 font-medium">Dashboard</span>
                </Link>
                <Link href="/campaigns" class="flex items-center px-6 py-3 text-gray-700 hover:bg-green-50 border-l-4 border-transparent hover:border-green-500">
                    <span class="ml-3 font-medium">Crowdfunding</span>
                </Link>
                <Link href="/jobs" class="flex items-center px-6 py-3 text-gray-700 hover:bg-green-50 border-l-4 border-transparent hover:border-green-500">
                    <span class="ml-3 font-medium">Jobs</span>
                </Link>
                <Link href="/market" class="flex items-center px-6 py-3 text-gray-700 hover:bg-green-50 border-l-4 border-transparent hover:border-green-500">
                    <span class="ml-3 font-medium">Marketplace</span>
                </Link>
            </nav>
        </aside>

        <!-- Main Content -->
        <div class="flex-1 flex flex-col">
            <header class="bg-white shadow-sm px-8 py-4 flex justify-between items-center">
                <h1 class="text-2xl font-bold text-gray-800">Make.ooo</h1>
                <div class="flex items-center space-x-6">
                    <span class="text-sm text-gray-600">{{ $page.props.auth.user.name }}</span>
                    <Link :href="route('logout')" method="post" class="text-green-600 hover:text-green-800 font-medium">Logout</Link>
                </div>
            </header>

            <main class="flex-1 p-8">
                <slot />
            </main>
        </div>
    </div>
</template>