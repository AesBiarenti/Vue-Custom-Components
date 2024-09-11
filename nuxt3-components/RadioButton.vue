<template>
    <label :class="['radio-container', labelStyle]">
      <input
        type="radio"
        :value="value"
        :checked="modelValue === value"
        @change="handleChange"
        :class="radioStyle"
        name="styled-radio-group"
      />
      <span class="radiomark"></span>
      <span class="label-text">{{ label }}</span>
    </label>
  </template>
  
  <script setup>
  const props = defineProps({
    label: {
      type: String,
      default: 'Option',
    },
    value: {
      type: String,
      required: true,
    },
    modelValue: {
      type: String,
      default: '',
    },
    radioStyle: {
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
    emits('update:modelValue', event.target.value);
  };
  </script>
  
  <style scoped>
  .radio-container {
    display: flex;
    align-items: center;
    cursor: pointer;
    position: relative;
    user-select: none;
  }
  
  .radio-container input {
    opacity: 0;
    position: absolute;
    cursor: pointer;
    height: 0;
    width: 0;
  }
  
  .radiomark {
    height: 20px;
    width: 20px;
    background-color: #fff;
    border: 2px solid #000;
    border-radius: 50%;
    transition: background-color 200ms ease, border-color 200ms ease;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }
  
  .radio-container input:checked ~ .radiomark {
    background-color: black;
    border-color: black;
  }
  
  .radiomark:after {
    content: '';
    position: absolute;
    display: none;
    width: 10px;
    height: 10px;
    background: white;
    border-radius: 50%;
  }
  
  .radio-container input:checked ~ .radiomark:after {
    display: block;
  }
  
  .label-text {
    margin-left: 8px;
    font-weight: 500;
    color: black;
  }
  </style>
  