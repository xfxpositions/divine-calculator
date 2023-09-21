<template>
  <div
    class="backdrop-blur-[24px] text-white bg-slate-50 bg-opacity-10 box-border py-3 px-4 select-none"
  >
    <div class="flex justify-around">
      <Button
        class="bg-slate-500 border-0 hover:bg-slate-600 box-border px-1 rounded-md bg-opacity-20"
        @click="memoryClean"
        >MC</Button
      >
      <Button
        class="bg-slate-500 border-0 hover:bg-slate-600 box-border px-1 rounded-md bg-opacity-20"
        @click="memoryRecall"
        >MR</Button
      >
      <Button
        class="bg-slate-500 border-0 hover:bg-slate-600 box-border px-1 rounded-md bg-opacity-20"
        @click="memoryAdd(total)"
        >M+</Button
      >
      <Button
        class="bg-slate-500 border-0 hover:bg-slate-600 box-border px-1 rounded-md bg-opacity-20"
        @click="memorySubtract(total)"
        >M-</Button
      >
      <Button
        class="bg-slate-500 border-0 hover:bg-slate-600 box-border px-1 rounded-md bg-opacity-20"
        @click="memorySet(total)"
        >MS</Button
      >
    </div>
  </div>
</template>

<script setup>
import { ref, defineProps, defineEmits } from "vue";

let memory = ref(0);

const { total } = defineProps({
  total: Number,
});

const emit = defineEmits(["recall"]);

function memoryClean() {
  memory.value = 0;
}

function memoryRecall() {
  // Emit the "recall" event with the memory value
  emit("recall", memory.value);
}

function memorySet(value) {
  memory.value = value;
}

function memoryAdd(value) {
  memory.value += value;
}

function memorySubtract(value) {
  memory.value -= value;
}
</script>
