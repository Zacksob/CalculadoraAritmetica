<script setup>

</script>

<template>
  <div id="app">
    <div class="calculator">
      <input v-model.number="operand1" type="number" placeholder="Enter first number" />
      <select v-model="operation">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <input v-model.number="operand2" type="number" placeholder="Enter second number" />
      <button @click="calculate">=</button>
      <input :value="result" disabled placeholder="Result" />
      <button @click="clear">C</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      operand1: null,
      operand2: null,
      operation: '+',
      result: null,
    };
  },
  methods: {
    calculate() {
      if (this.operation === '+') {
        this.result = this.operand1 + this.operand2;
      } else if (this.operation === '-') {
        this.result = this.operand1 - this.operand2;
      } else if (this.operation === '*') {
        this.result = this.operand1 * this.operand2;
      } else if (this.operation === '/') {
        if (this.operand2 !== 0) {
          this.result = this.operand1 / this.operand2;
        } else {
          this.result = 'Error: Division by zero';
        }
      }
    },
    clear() {
      this.operand1 = null;
      this.operand2 = null;
      this.operation = '+';
      this.result = null;
    },
  },
};
</script>

<style scoped>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f4f4f4;
}

.calculator {
  width: 300px;
  padding: 20px;
  background-color: #fff;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  gap: 10px;
}

input,
select,
button {
  height: 40px;
  font-size: 18px;
  padding: 5px;
  width: 100%;
  box-sizing: border-box;
}

button {
  background-color: #e0e0e0;
  border: none;
  cursor: pointer;
  transition: background-color 0.2s;
}

button:hover {
  background-color: #d0d0d0;
}

button:active {
  background-color: #c0c0c0;
}
</style>
