import SettingsButton from './SettingsButton.vue';
<template>
  <h2
    class="box-border py-3 px-4 backdrop-blur-[20px] text-white text-bold text-xl"
  >
    <NuxtLink class="cursor-default" to="/settings">
      <div
        class="inline-flex gap-1 justify-center items-center hover:bg-sky-200 hover:bg-opacity-40 rounded-md box-border box-border p-1 transition-all duration-300 ease-in-outbackdrop-blur-[20px]"
      >
        <SettingsButton class="inline"></SettingsButton>
      </div>
    </NuxtLink>
  </h2>
</template>
<style>
.white_color {
  filter: invert(100%) sepia(100%) saturate(0%) hue-rotate(269deg)
    brightness(107%) contrast(102%);
}
</style>
