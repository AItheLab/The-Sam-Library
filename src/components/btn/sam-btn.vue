<template>
    <button 
      :class="['sam-button', `sam-button--${type}`, { 'sam-button--with-icon': icon }]"
      @click="handleClick"
      :aria-label="icon && !label ? ariaLabel || undefined : undefined"
      :title="icon && !label ? ariaLabel || undefined : undefined">
      <Icon v-if="icon" :icon="icon" :style="{ fontSize: iconSize }" class="sam-button__icon" />
      {{ label }}
    </button>
  </template>
  
  <script setup lang="ts">
  import { withDefaults } from 'vue'
  import { Icon } from '@iconify/vue'
  
  interface IProps {
    label?: string;
    type: string;
    icon?: string;
    ariaLabel?: string;
    iconSize?: string;
  }
  
withDefaults(defineProps<IProps>(), {
    label: '',
    type: 'filled',
    icon: '',
    ariaLabel: '',
    iconSize: '1em' // Default icon size
  });
  
  const emits = defineEmits(['click']);
  
  const handleClick = (event: Event) => {
    emits('click', event);
  };
  </script>
  
  <style scoped lang="scss" src="./sam-btn.scss" />
  