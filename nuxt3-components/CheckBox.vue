<template>
    <label :class="['checkbox-container', labelStyle]">
      <input
        type="checkbox"
        :checked="modelValue"
        @change="handleChange"
        :class="checkboxStyle"
      />
      <span class="checkmark"></span>
      <span class="label-text">{{ label }}</span>
    </label>
  </template>
  
  <script setup>
  const props = defineProps({
    label: {
      type: String,
      default: 'Option',
    },
    modelValue: {
      type: Boolean,
      default: false,
    },
    checkboxStyle: {
      type: String,
      default: '',
    },
    labelStyle: {
      type: String,
      default: '',
    },
  });
  
  const emits = defineEmits(['update:modelValue']);
  
  const handleChange = (event) => {
    emits('update:modelValue', event.target.checked);
  };
  </script>
  
  <style scoped>
  .checkbox-container {
    display: flex;
    align-items: center;
    cursor: pointer;
    position: relative;
    user-select: none;
  }
  
  .checkbox-container input {
    opacity: 0;
    position: absolute;
    cursor: pointer;
    height: 0;
    width: 0;
  }
  
  .checkmark {
    height: 20px;
    width: 20px;
    background-color: #fff;
    border: 2px solid #000;
    border-radius: 4px;
    transition: background-color 200ms ease, border-color 200ms ease;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .checkbox-container input:checked ~ .checkmark {
    background-color: black;
    border-color: black;
  }
  
  .checkmark:after {
    content: '';
    position: absolute;
    display: none;
    width: 5px;
    height: 10px;
    border: solid white;
    border-width: 0 2px 2px 0;
    transform: rotate(45deg);
  }
  
  .checkbox-container input:checked ~ .checkmark:after {
    display: block;
  }
  
  .label-text {
    margin-left: 8px;
    font-weight: 500;
    color: black;
  }
  </style>
  