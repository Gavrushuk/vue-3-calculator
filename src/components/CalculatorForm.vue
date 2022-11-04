<script lang="ts" setup>
defineProps<{
  history: string;
  value: string;
}>();
</script>

<template>
  <div class="calculator-form">
    <div class="calculator-form__history">{{ history || '' }}</div>
    <div class="calculator-form__value">{{ value || 0 }}</div>
  </div>
</template>

<style lang="scss" scoped>
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
    color: #FFFFFF;
    opacity: 0.4;
  }
  .calculator-form__value {
    height: 96px;
    font-family: 'Work Sans';
    font-weight: 300;
    font-size: 96px;
    line-height: 96px;
    color: #FFFFFF;
    width: 100%;
    background-color: transparent;
    border: 0;
    text-align: right;
    overflow-x: auto;
    overflow-y: hidden;
    direction: rtl;
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
