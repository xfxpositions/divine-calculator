<template>
  <!-- background -->
  <div class="background w-full h-full -z-10">
    <!-- blur -->
    <div class="backdrop-blur-[20px] w-full h-full">
      <NuxtPage />
    </div>
  </div>
</template>
<style>
.background {
  background-image: url("/bg.jpg");
  object-fit: contain;
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}
</style>
