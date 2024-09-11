<template>
    <div class="timepicker-container">
      <input
        type="time"
        :value="modelValue"
        @input="updateValue($event.target.value)"
        :class="['primary-timepicker', inputStyle]"
        :min="minTime"
        :max="maxTime"
        :placeholder="placeholder"
      />
    </div>
  </template>
  
  <script setup>
  const props = defineProps({
    modelValue: {
      type: String,
      default: '',
    },
    minTime: {
      type: String,
      default: '',
    },
    maxTime: {
      type: String,
      default: '',
    },
    inputStyle: {
      type: String,
      default: '',
    },
    placeholder: {
      type: String,
      default: 'Select Time',
    },
  });
  
  const emits = defineEmits(['update:modelValue']);
  
  const updateValue = (value) => {
    emits('update:modelValue', value);
  };
  </script>
  
  <style scoped>
  .timepicker-container {
    display: flex;
    align-items: center;
  }
  
  .primary-timepicker {
    padding: 8px 20px;
    border: 1px solid rgb(200, 200, 200);
    border-radius: 5px;
    font-size: 1rem;
    transition: border-color 200ms ease, background-color 200ms ease;
    background-color: #f9f9f9;
    color: #333;
  }
  
  .primary-timepicker:hover {
    border-color: #999;
  }
  
  .primary-timepicker:focus {
    outline: none;
    border-color: black;
    background-color: #fff;
  }
  </style>
  