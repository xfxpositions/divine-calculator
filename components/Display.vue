<template>
  <ContextMenu :open="contextMenuOpen" />
  <div
    @contextmenu="contextHandler()"
    class="w-full h-24 backdrop-blur-lg cursor-default"
  >
    <div class="text-slate-300 font-bold text-right flex flex-col">
      <div class="mr-8 text-[18px] box-border pt-2">
        {{ prevValue }}{{ calculated ? " =" : "" }}
      </div>

      <span v-if="!ErrorMessage" class="mr-5 text-slate-300 text-[48px]">{{
        value == "" ? "0" : value
      }}</span>
      <span v-else class="mr-5 text-slate-300 text-[48px]">{{
        ErrorMessage
      }}</span>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";

const contextMenuOpen = ref(false);

function contextHandler(e) {
  contextMenuOpen.value = !contextMenuOpen.value;
  e.preventDefault();
  e.stopPropagation();
}

const { value, prevValue, calculated, ErrorMessage } = defineProps({
  value: String,
  prevValue: String,
  calculated: Boolean,
  ErrorMessage: String,
});
</script>
