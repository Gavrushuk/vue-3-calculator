<script lang="ts" setup>
import CalculatorButtons from '@/components/CalculatorButtons.vue';
import { ref } from 'vue';
import CalculatorForm from './CalculatorForm.vue';

const history = ref('');
const value = ref('')

function num(num: string) {
  value.value = value.value + num;
}

function clear() {
  value.value = '';
}

function remove() {
  value.value = value.value.slice(0, -1);
}
</script>

<template>
  <div class="calculator-content">
    <div class="calculator-display">
      <div></div>
      <CalculatorForm
        :history="history"
        :value="value"
      />
    </div>

    <CalculatorButtons
      @num="num"
      @clear="clear"
      @remove="remove"
    />
  </div>
</template>

<style lang="scss" scoped>
.calculator-content {
  background: #17171C;
  height: 100vh;
  width: 100%;
  padding: 20px;
  .calculator-display {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: calc(100% - 440px);
    margin-bottom: 16px;
  }
}
</style>
