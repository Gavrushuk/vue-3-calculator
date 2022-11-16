<script lang="ts" setup>
const emit = defineEmits<{
  (e: 'onChangeTheme'): void
}>();
</script>

<template>
  <div @click="emit('onChangeTheme')" class="calculator-theme-switcher">
    <img class="light-theme-icon" src="@/assets/light-theme-icon.svg" alt="">
    <img class="dark-theme-icon" src="@/assets/dark-theme-icon.svg" alt="">
    <div class="swiper"></div>
  </div>
</template>

<style lang="scss" scoped>
.light-theme {
  .calculator-theme-switcher {
    background: #FFFFFF;
    .dark-theme-icon {
      opacity: 0;
    }
    .swiper {
      transform: translateX(40px);
      background: #D2D3DA;
    }
  }
}

.dark-theme {
  .calculator-theme-switcher {
    background: #2E2F38;
    .light-theme-icon {
      opacity: 0;
    }
    .swiper {
      transform: translateX(0);
    }
  }
}

.calculator-theme-switcher {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-radius: 16px;
  padding: 4px;
  height: 32px;
  width: 72px;
  transition: 0.3s;
  cursor: pointer;
  .light-theme-icon,
  .dark-theme-icon {
    position: absolute;
    opacity: 1;
    transition: 0.3s;
  }
  .light-theme-icon {
    left: 8px;
  }
  .dark-theme-icon {
    right: 8px;
  }
  .swiper {
    position: absolute;
    left: 4px;
    background: #4E505F;
    border-radius: 50%;
    width: 24px;
    height: 24px;
    transition: all 0.3s;
  }
}
</style>
