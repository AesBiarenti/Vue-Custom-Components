<template>
    <button
      :class="['secondary-button', buttonStyle]"
      :type="type"
      @click="handleClick"
    >
      {{ label }}
    </button>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  
  // Props tanımla: label, type, buttonStyle
  const props = defineProps({
    label: {
      type: String,
      default: 'Secondary', // Buton metni
    },
    type: {
      type: String,
      default: 'button', // Buton tipi: button, submit, reset vb.
    },
    buttonStyle: {
      type: String,
      default: '', // Ekstra stil sınıfları eklenebilir
    },
  });
  
  const emits = defineEmits(['click']);
  
  // Tıklama olayını emit eder
  const handleClick = () => {
    emits('click');
  };
  </script>
  
  <style scoped>
  .secondary-button {
    background-color: white;
    border: 1px solid black;
    padding: 8px 20px;
    border-radius: 5px;
    color: black;
    font-weight: 500;
    transition: 200ms ease;
    margin: 5px;
    cursor: pointer;
    text-decoration: none;
    min-width: 100px;
  }
  
  .secondary-button:hover {
    background-color: rgb(240, 240, 240);
  }
  
  .secondary-button:active {
    background-color: rgb(220, 220, 220);
    transform: scale(0.95);
  }
  </style>
  