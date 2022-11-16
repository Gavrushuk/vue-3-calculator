<script lang="ts" setup>
defineProps<{
  history: string;
  currentValue: string;
  answer: string;
}>();
</script>

<template>
  <div class="calculator-form">
    <div class="calculator-form__history">{{ `${history}${currentValue}` || 0 }}</div>
    <div class="calculator-form__value">{{ answer || '' }}</div>
  </div>
</template>

<style lang="scss" scoped>
.light-theme {
  .calculator-form__history,
  .calculator-form__value {
    color: #000000;
  }
}

.dark-theme {
  .calculator-form__history,
  .calculator-form__value {
    color: #FFFFFF;
  }
}

.calculator-form {
  display: flex;
  flex-direction: column;
  gap: 16px;
  .calculator-form__history {
    height: 47px;
    font-family: 'Work Sans';
    font-weight: 300;
    font-size: 40px;
    line-height: 47px;
    opacity: 0.4;
    direction: ltr !important;
  }
  .calculator-form__value {
    height: 80px;
    font-family: 'Work Sans';
    font-weight: 300;
    font-size: 80px;
    line-height: 80px;
    width: 100%;
    background-color: transparent;
    border: 0;
  }
  .calculator-form__history,
  .calculator-form__value {
    text-align: right;
    overflow-x: auto;
    overflow-y: hidden;
    transition: 0.3s;
    &::-webkit-scrollbar {
      height: 5px;
      border-radius: 5px;
    }
    &::-webkit-scrollbar-track {
      background: rgba($color: #f1f1f1, $alpha: 0.1);
      border-radius: 5px;
    }
    &::-webkit-scrollbar-thumb {
      background: #888;
      border-radius: 5px;
    }
    &::-webkit-scrollbar-thumb:hover {
      background: #555;
      border-radius: 5px;
    }
  }
}
</style>
