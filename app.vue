<template>
  <!-- background -->
  <ClientOnly>
    <div class="background w-full h-full -z-10">
      <!-- blur -->
      <div class="backdrop-blur-[20px] w-full h-full">
        <NuxtPage />
      </div>
    </div>
  </ClientOnly>
</template>
<script setup>
import "@/assets/css/main.css";
</script>
<style>
body {
  height: 100vh;
}
</style>
