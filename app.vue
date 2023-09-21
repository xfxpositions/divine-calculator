<template>
  <!-- main container -->
  <div
    class="bg w-full flex flex-col gap-4 items-center justify-center h-[100vh] overflow-hidden bg-slate-300 bg-opacity-30 dark:bg-slate-500 dark:bg-opacity-40"
  >
    <p>Xfx Calculator Web demo</p>

    <!-- background -->
    <div
      class="background max-w-[420px] w-[420px] overflow-hidden rounded-md shadow app-shadow"
    >
      <!-- blur -->
      <div class="backdrop-blur-[20px]">
        <NuxtPage />
      </div>
    </div>
    <div class="flex gap-5 justify-center items-center">
      <a
        href="https://github.com/xfxpositions/divine-calculator"
        class="underline"
        >Source Code</a
      >
      <a href="https://tr.yusufkaraca.dev" class="underline"
        >Made by Yusuf Karaca</a
      >
    </div>
  </div>
</template>
<script setup>
import "@/assets/css/main.css";
</script>
<style>
.bg {
  box-shadow: rgba(50, 50, 93, 0.25) 0px 30px 60px -12px inset,
    rgba(0, 0, 0, 0.3) 0px 18px 36px -18px inset;
}

/* .shadow::after {
  content: "";
  pointer-events: none;
  position: absolute;
  border-radius: 0.375rem;
  top: -2px;
  left: -2px;
  --bg-size: 300%;
  --color-one: rgb(222, 26, 26);
  --color-two: rgb(77, 126, 211);
  background: linear-gradient(
      -45deg,
      var(--color-one),
      var(--color-two),
      var(--color-one)
    )
    0 0 / var(--bg-size) 100%;
  width: calc(100% + 8px);
  height: calc(100% + 4px);
  z-index: -1;
  animation: animate 30s linear infinite;
  mix-blend-mode: difference;
  opacity: 50%;
}
@keyframes animate {
  0% {
    background-position: 300% 0;
  }

  100% {
    background-position: 0 0;
  }
} */
</style>
