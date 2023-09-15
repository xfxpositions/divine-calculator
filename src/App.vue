<template>
  <!-- container -->
  <div class="rounded-lg overflow-hidden">
    <!-- background image -->
    <div class="background w-full h-full">
      <!-- display -->
      <Display :value="total" />
      <div class="h-full flex flex-col flex-wrap">
        <div
          class="buttons flex flex-1 flex-wrap transition-all 1s ease-in-out backdrop-blur-[20px] text-white"
        >
          <Button @click="clear()" class="flex-1 h-20 backdrop-blur-2xl"
            >C</Button
          >
          <Button
            @click="setOperator(operators.Negatate)"
            class="flex-1 h-20 backdrop-blur-2xl"
            >+/-</Button
          >
          <Button
            @click="setOperator(operators.Percent)"
            class="flex-1 h-20 backdrop-blur-2xl"
            >%</Button
          >
          <Button
            @click="setOperator(operators.Divide)"
            class="flex-1 h-20 bg-sky-400 bg-opacity-20"
            >/</Button
          >
        </div>
        <div
          class="buttons w-full flex flex-1 flex-wrap transition-all 1s ease-in-out backdrop-blur-[20px] text-white"
        >
          <Button
            @click="append($event, 7)"
            class="flex-1 h-20 backdrop-blur-2xl"
            >7</Button
          >
          <Button
            @click="append($event, 8)"
            class="flex-1 h-20 backdrop-blur-2xl"
            >8</Button
          >
          <Button
            @click="append($event, 9)"
            class="flex-1 h-20 backdrop-blur-2xl"
            >9</Button
          >
          <Button
            @click="setOperator(operators.Multiplication)"
            class="flex-1 h-20 bg-sky-400 bg-opacity-20"
            >X</Button
          >
        </div>
        <div
          class="buttons w-full flex flex-1 flex-wrap transition-all 1s ease-in-out backdrop-blur-[20px] text-white"
        >
          <Button
            @click="append($event, 4)"
            class="flex-1 h-20 backdrop-blur-2xl"
            >4</Button
          >
          <Button
            @click="append($event, 5)"
            class="flex-1 h-20 backdrop-blur-2xl"
            >5</Button
          >
          <Button
            @click="append($event, 6)"
            class="flex-1 h-20 backdrop-blur-2xl"
            >6</Button
          >
          <Button
            @click="setOperator(operators.Subtraction)"
            class="flex-1 h-20 bg-sky-400 bg-opacity-20"
            >-</Button
          >
        </div>
        <div
          class="buttons w-full flex flex-1 flex-wrap transition-all 1s ease-in-out backdrop-blur-[20px] text-white"
        >
          <Button
            @click="append($event, 1)"
            class="flex-1 h-20 backdrop-blur-2xl"
            >1</Button
          >
          <Button
            @click="append($event, 2)"
            class="flex-1 h-20 backdrop-blur-2xl"
            >2</Button
          >
          <Button
            @click="append($event, 3)"
            class="flex-1 h-20 backdrop-blur-2xl"
            >3</Button
          >
          <Button
            @click="setOperator(operators.Sum)"
            class="flex-1 h-20 bg-sky-400 bg-opacity-20"
            >+</Button
          >
        </div>
        <div
          class="buttons w-full grid grid-cols-4 flex-1 flex-wrap transition-all 1s ease-in-out backdrop-blur-[20px] text-white"
        >
          <Button
            @click="append($event, 0)"
            class="col-span-2 h-20 backdrop-blur-2xl"
            >0</Button
          >
          <Button
            @click="append($event, '=')"
            class="col-span-1 h-20 backdrop-blur-2xl"
            >.</Button
          >
          <Button
            @click="setOperator(operators.Calculate)"
            class="col-span-1 h-20 bg-sky-400 bg-opacity-20"
            >=</Button
          >
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import Button from "./components/Button.vue";
import Display from "./components/Display.vue";

const operators = {
  Sum: "sum",
  Subtraction: "subtraction",
  Calculate: "calculate",
  Multiplication: "multiplication",
  Divide: "divide",
  Percent: "percent",
  Negatate: "negatate",
};

const total = ref("");

function clear() {
  total.value = "";
}

function negatate() {
  total.value = -total.value;
}

function append(event, val) {
  console.log(event.target.innerText);
  total.value += event.target.innerText;
  console.log(`total = ${total.value}`);
}
</script>
<style scoped>
.background {
  max-width: 500px;
  max-height: 1200px;
  background-image: url("src/public/bg.jpg");
  object-fit: contain;
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}
</style>
