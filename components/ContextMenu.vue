<template>
  <div class="flex flex-col gap-1" :class="{ hidden: !open }">
    <p class="text-md font-semibold">Copy</p>
    <p class="text-md font-semibold">Paste</p>
  </div>
</template>
<script setup>
const { open } = defineProps({
  open: Boolean,
});
</script>
