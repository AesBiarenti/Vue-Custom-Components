<template>
    <button
      :class="['base-button', buttonStyle]"
      :style="{ backgroundColor: color, padding: padding, fontSize: size }"
      @click="handleClick"
    >
      {{ label }}
    </button>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  
  const props = defineProps({
    label: {
      type: String,
      default: 'Button',
    },
    color: {
      type: String,
      default: 'black',
    },
    padding: {
      type: String,
      default: '8px 20px',
    },
    size: {
      type: String,
      default: '16px',
    },
    buttonStyle: {
      type: String,
      default: '',
    },
  });
  
  const emits = defineEmits(['click']);
  
  const handleClick = () => {
    emits('click');
  };
  </script>
  
  <style scoped>
  .base-button {
    border: 0;
    border-radius: 5px;
    color: white;
    font-weight: 500;
    transition: 200ms ease;
    margin: 5px;
    cursor: pointer;
    text-decoration: none;
    min-width: 100px;
  }
  
  .base-button:hover {
    filter: brightness(90%);
  }
  
  .base-button:active {
    filter: brightness(80%);
    transform: scale(0.93);
  }
  </style>
  