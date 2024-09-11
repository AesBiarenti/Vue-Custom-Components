<template>
    <button
      :class="['bordered-button', buttonStyle]"
      :type="type"
      @click="handleClick"
    >
      {{ label }}
    </button>
  </template>
  
  <script setup>
  const props = defineProps({
    label: {
      type: String,
      default: 'Bordered', // Buton metni
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
  .bordered-button {
    background-color: transparent;
    border: 2px solid black;
    padding: 8px 20px;
    border-radius: 5px;
    color: black;
    font-weight: 500;
    transition: 200ms ease;
    margin: 5px;
    cursor: pointer;
    min-width: 100px;
  }
  
  .bordered-button:hover {
    background-color: black;
    color: white;
  }
  
  .bordered-button:active {
    background-color: rgb(40, 40, 40);
    transform: scale(0.95);
  }
  </style>
  