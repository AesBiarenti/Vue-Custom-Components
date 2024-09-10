<template>
    <input
      :type="type"
      :value="modelValue"
      :placeholder="placeholder"
      :class="['primary-input', inputStyle]"
      @input="$emit('update:modelValue', $event.target.value)"
    />
  </template>
  
  <script setup>
  import { defineProps, defineEmits } from 'vue';
  
  const props = defineProps({
    type: {
      type: String,
      default: 'text',
    },
    modelValue: {
      type: String,
      default: '',
    },
    placeholder: {
      type: String,
      default: 'Enter value',
    },
    inputStyle: {
      type: String,
      default: '',
    },
  });
  
  const emits = defineEmits(['update:modelValue']);
  </script>
  
  <style scoped>
  .primary-input {
    border-radius: 5px;
    border: none;
    padding: 8px 20px;
    transition: 200ms;
    background-color: rgb(243, 243, 243);
  }
  
  .primary-input:hover {
    background-color: rgb(226, 226, 226);
  }
  
  .primary-input:focus {
    border: 2px solid rgb(200, 200, 200);
    outline: none;
  }
  </style>
  