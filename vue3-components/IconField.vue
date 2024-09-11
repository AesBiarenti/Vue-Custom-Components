<template>
    <div class="iconfield-container">
      <span class="icon" v-if="icon">
        <component :is="icon" class="input-icon" />
      </span>
      <input
        :type="type"
        :placeholder="placeholder"
        :value="modelValue"
        @input="updateValue($event.target.value)"
        class="iconfield-input"
      />
    </div>
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  
  const props = defineProps({
    modelValue: {
      type: String,
      default: '',
    },
    placeholder: {
      type: String,
      default: 'Enter text',
    },
    icon: {
      type: [String, Object], // İkon component'i veya ismi
      default: '',
    },
    type: {
      type: String,
      default: 'text',
    },
  });
  
  const emits = defineEmits(['update:modelValue']);
  
  const updateValue = (value) => {
    emits('update:modelValue', value);
  };
  </script>
  
  <style scoped>
  .iconfield-container {
    display: flex;
    align-items: center;
    border: 1px solid rgb(200, 200, 200);
    border-radius: 5px;
    padding: 8px;
    background-color: #f9f9f9;
    transition: border-color 200ms ease;
  }
  
  .input-icon {
    margin-right: 10px;
    color: #333;
    font-size: 1.2rem;
  }
  
  .iconfield-input {
    border: none;
    outline: none;
    flex: 1;
    background: transparent;
    font-size: 1rem;
    color: #333;
  }
  
  .iconfield-container:hover {
    border-color: #999;
  }
  
  .iconfield-container:focus-within {
    border-color: black;
  }
  </style>
  