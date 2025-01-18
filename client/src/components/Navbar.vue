<script setup>
import Logo from './Logo.vue';
import { RouterLink, useRoute } from 'vue-router';

const isActive = (route) => {
  return useRoute().path === route;
}
const classRouteActive =
  (route) => isActive(route) ? ' bg-green-900 hover:bg-gray-900' : 'text-white hover:bg-green-900 hover:text-white';

const classRoute = "text-white rounded-md px-3 py-2"
</script>
<template>
  <nav class="bg-green-700 border-b border-green-500">
    <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
      <div class="flex h-20 items-center justify-between">
        <div class="flex flex-1 items-center justify-center md:items-stretch md:justify-start">
          <Logo />
          <div class="md:ml-auto">
            <div class="flex space-x-2">
              <RouterLink to="/" :class="[classRouteActive('/'),classRoute]">Home</RouterLink>
              <RouterLink to="/jobs" :class="[classRouteActive('/jobs'),classRoute]">Jobs
              </RouterLink>
              <RouterLink to="/jobs/add" :class="[classRouteActive('/jobs/add'),classRoute]">Add
                Job</RouterLink>
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>