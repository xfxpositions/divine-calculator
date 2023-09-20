<template>
  <div
    class="backdrop-blur-[24px] text-white bg-slate-50 bg-opacity-10 box-border py-3 px-4 select-none"
  >
    <NuxtLink
      class="cursor-default inline-flex gap-1 justify-center items-center hover:bg-sky-200 hover:bg-opacity-40 rounded-md box-border box-border p-1 transition-all duration-300 ease-in-outbackdrop-blur-[20px]"
      to="/"
    >
      <img src="/goback.svg" alt="goback" />
    </NuxtLink>
    <h1 class="text-2xl font-bold">Settings</h1>
    <!-- <hr /> -->
    <!-- <div class="bg-black h-[1px] w-full" /> -->
    <br />
    <h2 class="text-xl font-bold">Appearance</h2>
    <!-- background file picker -->
    <h3 class="text-md font-semibold">Background Image</h3>
    <br />
    <div class="flex items-center justify-center w-full">
      <label
        for="dropzone-file"
        class="flex flex-col items-center justify-center w-full h-64 border-2 border-gray-300 border-dashed rounded-lg cursor-pointer bg-gray-400 transition-all duration-300 ease-in-out dark:hover:bg-bray-800 dark:bg-gray-800 hover:bg-gray-400 dark:border-gray-700 dark:hover:border-gray-500 dark:hover:bg-gray-900 bg-opacity-20 dark:bg-opacity-60 dark:hover:bg-opacity-70"
      >
        <div class="flex flex-col items-center justify-center pt-5 pb-6">
          <svg
            class="w-8 h-8 mb-4 text-gray-500 dark:text-gray-400"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 20 16"
          >
            <path
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M13 13h3a3 3 0 0 0 0-6h-.025A5.56 5.56 0 0 0 16 6.5 5.5 5.5 0 0 0 5.207 5.021C5.137 5.017 5.071 5 5 5a4 4 0 0 0 0 8h2.167M10 15V6m0 0L8 8m2-2 2 2"
            />
          </svg>
          <p class="mb-2 text-sm text-gray-500 dark:text-gray-400">
            <span class="font-semibold">Click to upload</span> or drag and drop
          </p>
          <p class="text-xs text-gray-500 dark:text-gray-400">
            SVG, PNG, JPG or GIF
          </p>
        </div>
        <input id="dropzone-file" type="file" class="hidden" />
      </label>
    </div>
    <!-- set defaults -->
    <br />
    <button
      class="bg-gray-700 bg-opacity-50 hover:bg-opacity-90 rounded-md transition-all duration-300 ease-in-out text-white cursor-default box-border px-3 py-2"
    >
      Set to Defaults
    </button>
    <br />
    <br />

    <h2 class="text-xl font-bold">About</h2>
    <br />
    <p>Xfx Calculator 0.2.0 alpha.</p>
    <a href="https://github.com/xfxpositions/xfxcalc" class="underline"
      >Github repository.</a
    >
    <p>
      Made with love by
      <a href="https://yusufkaraca.dev" class="underline">Yusuf Karaca</a>
      .
    </p>
  </div>
</template>
