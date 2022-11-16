<script lang="ts" setup>
import CalculatorButtons from '@/components/CalculatorButtons.vue';
import { onMounted, ref } from 'vue';
import CalculatorForm from './CalculatorForm.vue';
import CalculatorThemeSwitcher from './CalculatorThemeSwitcher.vue';

const theme = ref('dark-theme');
const history = ref('');
const currentValue = ref('');
const answer = ref('')
const operatorClicked = ref(true);

function clear() {
  history.value = '';
  currentValue.value = '';
  answer.value = ''
  operatorClicked.value = true;
}

function sign() {
  if (!currentValue.value) return;

  currentValue.value = currentValue.value.charAt(0) === '-' ? currentValue.value.slice(1) : `-${currentValue.value}`;
}

function percent() {
  if (!currentValue.value) return;

  currentValue.value = `${parseFloat(currentValue.value) / 100}`;
}

function divide() {
  addToHistory('/');
}

function multiply() {
  addToHistory('*');
}

function minus() {
  addToHistory('-');
}

function plus() {
  addToHistory('+');
}

function equal() {
  if (!operatorClicked.value) {
    answer.value = eval(history.value + currentValue.value);
  }
}

function num(num: string) {
  if (operatorClicked.value) {
    currentValue.value = '';
    operatorClicked.value = false;
  }

  if (answer.value) {
    answer.value = '';
  }

  currentValue.value = `${currentValue.value}${num}`;
}

function dot() {
  if (currentValue.value.indexOf('.') === -1) {
    num('.');
  }
}

function addToHistory(operator: string) {
  if (operatorClicked.value) return;

  history.value += `${currentValue.value}${operator}`;
  currentValue.value = '';
  operatorClicked.value = true;
}

function onChangeTheme() {
  theme.value = theme.value === 'dark-theme' ? 'light-theme' : 'dark-theme';
}

onMounted(() => {

});
</script>

<template>
  <div
    class="calculator-content"
    :class="[theme]"
  >
    <div class="calculator-display">
      <div class="calculator-theme-switcher-wrapper">
        <CalculatorThemeSwitcher @onChangeTheme="onChangeTheme" />
      </div>

      <CalculatorForm
        :history="history"
        :currentValue="currentValue"
        :answer="answer"
      />
    </div>

    <CalculatorButtons
      @clear="clear"
      @sign="sign"
      @percent="percent"
      @divide="divide"
      @multiply="multiply"
      @minus="minus"
      @plus="plus"
      @num="num"
      @dot="dot"
      @equal="equal"
    />
  </div>
</template>

<style lang="scss" scoped>
.calculator-content {
  height: 100vh;
  width: 100%;
  padding: 20px;
  transition: 0.3s;
  &.light-theme {
    background: #F1F2F3;
  }
  &.dark-theme {
    background: #17171C;
  }
  .calculator-display {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: calc(100% - 440px);
    margin-bottom: 16px;
    .calculator-theme-switcher-wrapper {
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }
}
</style>
