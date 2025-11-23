<script setup lang="ts">
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
</script>

<template>
  <div>
    <h2 class="text-3xl font-bold text-make-gray mb-8">Welcome back!</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <div class="bg-white p-8 rounded-lg shadow hover:shadow-xl transition">
        <h3 class="text-xl font-bold text-make-orange">Start a Campaign</h3>
        <p class="text-gray-600 mt-2">Launch your idea to the world</p>
      </div>
      <div class="bg-white p-8 rounded-lg shadow hover:shadow-xl transition">
        <h3 class="text-xl font-bold text-make-blue">Find Jobs</h3>
        <p class="text-gray-600 mt-2">Work with the best makers</p>
      </div>
      <div class="bg-white p-8 rounded-lg shadow hover:shadow-xl transition">
        <h3 class="text-xl font-bold text-make-gray">Marketplace</h3>
        <p class="text-gray-600 mt-2">Coming soon</p>
      </div>
    </div>
  </div>
</template>
