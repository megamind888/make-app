<script setup lang="ts">
import { ref } from 'vue';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';
import { Link } from '@inertiajs/vue3';

const showingNavigationDropdown = ref(false);
</script>

<template>
  <div class="min-h-screen bg-make-light flex">
    <!-- Sidebar -->
    <aside class="w-64 bg-white shadow-lg">
      <div class="p-6">
        <ApplicationLogo />
      </div>
      <nav class="mt-6">
        <Link :href="route('dashboard')" class="flex items-center px-6 py-3 text-make-gray hover:bg-make-light">
          <span>Dashboard</span>
        </Link>
        <Link href="/campaigns" class="flex items-center px-6 py-3 text-make-gray hover:bg-make-light">
          Crowdfunding
        </Link>
        <Link href="/jobs" class="flex items-center px-6 py-3 text-make-gray hover:bg-make-light">
          Jobs
        </Link>
      </nav>
    </aside>

    <!-- Main content -->
    <div class="flex-1 flex flex-col">
      <header class="bg-white shadow-sm border-b border-gray-200 px-8 py-4 flex justify-between items-center">
        <h1 class="text-xl font-semibold text-make-gray">Make.ooo</h1>
        <div class="flex items-center space-x-4">
          <span class="text-sm text-gray-600">{{ $page.props.auth.user.name }}</span>
          <Link :href="route('logout')" method="post" class="text-sm text-make-orange hover:underline">Logout</Link>
        </div>
      </header>
      <main class="flex-1 p-8">
        <slot />
      </main>
    </div>
  </div>
</template>
