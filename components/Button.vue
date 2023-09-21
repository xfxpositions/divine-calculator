<template>
  <button
    class="btn text-2xl font-semibold transition-all ease-in-out duration-300 backdrop-blur-lg hover:backdrop-blur-sm flex items-center justify-center cursor-default border-black border-[1px] border-solid border-collapse"
  >
    <slot />
  </button>
</template>
<style scoped>
.btn:hover {
  /* filter: blur(1px); */
  backdrop-filter: blur(10px);
}
</style>
