<script setup>

</script>

<template>
  <div id="app">
    <div class="calculator">
      <input v-model="current" disabled />
      <div class="buttons">
        <button @click="clear">C</button>
        <button @click="append('/')">/</button>
        <button @click="append('*')">*</button>
        <button @click="backspace">←</button>
        <button @click="append('7')">7</button>
        <button @click="append('8')">8</button>
        <button @click="append('9')">9</button>
        <button @click="append('-')">-</button>
        <button @click="append('4')">4</button>
        <button @click="append('5')">5</button>
        <button @click="append('6')">6</button>
        <button @click="append('+')">+</button>
        <button @click="append('1')">1</button>
        <button @click="append('2')">2</button>
        <button @click="append('3')">3</button>
        <button @click="calculate">=</button>
        <button @click="append('0')">0</button>
        <button @click="append('.')">.</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: '',
    };
  },
  methods: {
    append(char) {
      this.current += char;
    },
    clear() {
      this.current = '';
    },
    backspace() {
      this.current = this.current.slice(0, -1);
    },
    calculate() {
      try {
        this.current = eval(this.current).toString();
      } catch (e) {
        this.current = 'Error';
      }
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
  width: 400px;
  padding: 20px;
  background-color: #fff;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}

input {
  width: 100%;
  height: 50px;
  font-size: 24px;
  text-align: right;
  margin-bottom: 10px;
  padding: 5px;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

button {
  width: 100%;
  height: 50px;
  font-size: 18px;
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
