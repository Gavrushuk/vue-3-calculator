<script lang="ts" setup>
import IconSign from './icons/IconSign.vue';

const emit = defineEmits<{
  (e: 'clear'): void;
  (e: 'sign'): void;
  (e: 'percent'): void;
  (e: 'divide'): void;
  (e: 'multiply'): void;
  (e: 'minus'): void;
  (e: 'plus'): void;
  (e: 'num', num: string): void;
  (e: 'dot'): void;
  (e: 'equal'): void;
}>();
</script>

<template>
  <div class="calculator-buttons">
    <button @click="emit('clear')" class="calculator-button">C</button>
    <button @click="emit('sign')" class="calculator-button">
      <IconSign />
    </button>
    <button @click="emit('percent')" class="calculator-button">%</button>
    <button @click="emit('divide')" class="calculator-button">÷</button>

    <button @click="emit('num', '7')" class="calculator-button">7</button>
    <button @click="emit('num', '8')" class="calculator-button">8</button>
    <button @click="emit('num', '9')" class="calculator-button">9</button>
    <button @click="emit('multiply')" class="calculator-button">×</button>

    <button @click="emit('num', '4')" class="calculator-button">4</button>
    <button @click="emit('num', '5')" class="calculator-button">5</button>
    <button @click="emit('num', '6')" class="calculator-button">6</button>
    <button @click="emit('minus')" class="calculator-button">-</button>

    <button @click="emit('num', '1')" class="calculator-button">1</button>
    <button @click="emit('num', '2')" class="calculator-button">2</button>
    <button @click="emit('num', '3')" class="calculator-button">3</button>
    <button @click="emit('plus')" class="calculator-button">+</button>

    <button @click="emit('num', '0')" class="calculator-button">0</button>
    <button @click="emit('dot')" class="calculator-button">.</button>
    <button @click="emit('equal')" class="calculator-button">=</button>
  </div>
</template>

<style lang="scss" scoped>
.light-theme {
  .calculator-buttons {
    .calculator-button {
      background: #FFFFFF;
      color: #000000;
      &:nth-child(1),
      &:nth-child(2),
      &:nth-child(3),
      &:nth-child(4) {
        background: #D2D3DA;
      }
    }
  }
}

.dark-theme {
  .calculator-buttons {
    .calculator-button {
      background: #2E2F38;
      color: #ffffff;
      &:nth-child(1),
      &:nth-child(2),
      &:nth-child(3),
      &:nth-child(4) {
        background: #4E505F;
      }
    }
  }
}

.calculator-buttons {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  .calculator-button {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 72px;
    color: #FFFFFF;
    background: #2E2F38;
    border-radius: 24px;
    padding: 12px;
    border: none;
    width: calc(25% - 12px);
    font-family: 'Work Sans';
    font-weight: 400;
    font-size: 32px;
    line-height: 40px;
    user-select: none;
    transition: 0.3s;
    cursor: pointer;
    &:nth-child(4n),
    &:last-child {
      background: #4B5EFC !important;
      color: #ffffff !important;
    }
    &:nth-child(17) {
      width: calc((25% - 4px) * 2);
    }
  }
}
</style>
