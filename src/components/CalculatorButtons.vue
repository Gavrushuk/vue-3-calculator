<script lang="ts" setup>
const emit = defineEmits<{
  (e: 'num', num: string): void,
  (e: 'operator', num: string): void,
  (e: 'clear'): void,
  (e: 'remove'): void,
}>();
</script>

<template>
  <div class="calculator-buttons">
    <button @click="emit('clear')" class="calculator-button">C</button>
    <button class="calculator-button">±</button>
    <button class="calculator-button">%</button>
    <button class="calculator-button">÷</button>

    <button @click="emit('num', '7')" class="calculator-button">7</button>
    <button @click="emit('num', '8')" class="calculator-button">8</button>
    <button @click="emit('num', '9')" class="calculator-button">9</button>
    <button class="calculator-button">x</button>

    <button @click="emit('num', '4')" class="calculator-button">4</button>
    <button @click="emit('num', '5')" class="calculator-button">5</button>
    <button @click="emit('num', '6')" class="calculator-button">6</button>
    <button class="calculator-button">-</button>

    <button @click="emit('num', '1')" class="calculator-button">1</button>
    <button @click="emit('num', '2')" class="calculator-button">2</button>
    <button @click="emit('num', '3')" class="calculator-button">3</button>
    <button class="calculator-button">+</button>

    <button class="calculator-button">.</button>
    <button class="calculator-button">0</button>
    <button @click="emit('remove')" class="calculator-button">⌫</button>
    <button class="calculator-button">=</button>
  </div>
</template>

<style lang="scss" scoped>
.calculator-buttons {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  .calculator-button {
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
    cursor: pointer;
    &:nth-child(1),
    &:nth-child(2),
    &:nth-child(3),
    &:nth-child(4) {
      background: #4E505F;
    }
    &:nth-child(4n) {
      background: #4B5EFC;
    }
    &:disabled {

    }
  }
}
</style>
