<template>
  <!-- container -->
  <div
    class="rounded-lg overflow-hidden"
    @paste="onPasteHandler()"
    @copy="onCopyHandler()"
  >
    <!-- background image -->
    <div class="" @paste="onPasteHandler()" @copy="onCopyHandler()">
      <!-- display -->
      <HeadSection />
      <Display :value="total" :prevValue="prevValue" :calculated="calculated" />
      <Memory :total="Number(total)" @recall="memoryRecallHandler" />
      <div class="h-full flex flex-col flex-wrap">
        <div
          class="buttons flex flex-1 flex-wrap transition-all 1s ease-in-out backdrop-blur-[20px] text-white"
        >
          <Button @click="clear()" class="flex-1 h-20 backdrop-blur-2xl"
            >C</Button
          >
          <Button @click="negatate()" class="flex-1 h-20 backdrop-blur-2xl"
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
            @click="calculate()"
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
import isNumber from "is-number";

const operators = {
  Sum: {
    name: "Sum",
    symbol: "+",
    perform: function (x, y) {
      return x + y;
    },
  },
  Subtraction: {
    name: "Subtraction",
    symbol: "-",
    perform: function (x, y) {
      return x - y;
    },
  },
  Calculate: {
    name: "Calculate",
    symbol: "=",
    perform: function (x, y) {
      return x; // Just returns the first number for demonstration
    },
  },
  Multiplication: {
    name: "Multiplication",
    symbol: "*",
    perform: function (x, y) {
      return x * y;
    },
  },
  Divide: {
    name: "Divide",
    symbol: "/",
    perform: function (x, y) {
      if (y === 0) {
        return "Cannot divide by zero";
      }
      return x / y;
    },
  },
  Percent: {
    name: "Percent",
    symbol: "%",
    perform: function (x, y) {
      return (x * y) / 100;
    },
  },
  Empty: {
    name: "Empty",
    symbol: "",
    perform: function (x, y) {
      return "No operation specified";
    },
  },
};
const prevValue = ref("");
const total = ref("");

// after the setOperator, this would be true for re-defining in the next append
// total: 99, set operator to sum,
// next append -> total: append.value
const setted = ref(false);
const currentOperator = ref(operators.Empty);
const previousOperator = ref(operators.Empty);

const calculated = ref(false);

function onPasteHandler(e) {
  navigator.clipboard.readText().then((text) => {
    if (isNumber(text)) {
      total.value = text;
    }
    console.log(text);
  });
}

function onCopyHandler(e) {
  navigator.clipboard.writeText(total.value);
  console.log("copied");
}

function memoryRecallHandler(memory) {
  console.log(memory);

  total.value = memory.toString();
}

function calculate() {
  if (currentOperator.value !== operators.Empty) {
    try {
      const x = parseFloat(prevValue.value);
      const y = parseFloat(total.value);
      const result = currentOperator.value.perform(x, y);
      prevValue.value += ` ${total.value}`;
      total.value = result.toString();
      calculated.value = true;
    } catch (error) {
      total.value = "Error";
      console.error("Calculation error:", error);
    }
  }
}

function setOperator(newOperator) {
  previousOperator.value = currentOperator.value;
  currentOperator.value = newOperator;

  if (
    previousOperator.value.symbol == operators.Subtraction.symbol &&
    currentOperator.value.symbol == operators.Sum.symbol
  ) {
    total.value = Number(-total.value).toString();
  }
  prevValue.value = `${total.value}\u00A0${currentOperator.value.symbol}`;
  setted.value = true;
}

function clear() {
  prevValue.value = "";
  total.value = "";
  currentOperator.value = operators.Empty;
  setted.value = false;
  calculated.value = false;
}

function negatate() {
  total.value = -total.value;
}

function append(event, val) {
  if (total.value === "0") {
    total.value = "";
  }
  if (setted.value) {
    total.value = "";
    setted.value = false;
  }
  // don't add more than one '.' character
  if (total.value.includes(".") && event.target.innerText == ".") return;
  console.log(event.target.innerText);
  total.value += event.target.innerText;
  console.log(`total = ${total.value}`);
}
</script>
<style scoped>
.background {
  max-width: 500px;
  max-height: 1200px;
  background-image: url("/bg.jpg");
  object-fit: contain;
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}
</style>
