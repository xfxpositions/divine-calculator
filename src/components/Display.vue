<template>
  <div class="w-full h-24 backdrop-blur-lg cursor-default">
    <div class="text-slate-300 font-bold text-right flex flex-col">
      <div class="mr-8 text-[18px] box-border pt-2">
        {{ prevValue }}
      </div>

      <span class="mr-5 text-slate-300 text-[48px]">{{
        value == "" ? "0" : value
      }}</span>
    </div>
  </div>
  <div></div>
</template>
<script setup>
import { ref } from "vue";

const { value } = defineProps({
  value: String,
});
const prevValue = ref(null);
</script>
