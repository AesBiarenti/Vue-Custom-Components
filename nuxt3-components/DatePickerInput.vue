<template>
    <div class="datepicker-container">
      <input
        type="date"
        :value="modelValue"
        @input="updateValue($event.target.value)"
        :class="['primary-datepicker', inputStyle]"
        :min="minDate"
        :max="maxDate"
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
    minDate: {
      type: String,
      default: '',
    },
    maxDate: {
      type: String,
      default: '',
    },
    inputStyle: {
      type: String,
      default: '',
    },
    placeholder: {
      type: String,
      default: 'Select Date',
    },
  });
  
  const emits = defineEmits(['update:modelValue']);
  
  const updateValue = (value) => {
    emits('update:modelValue', value);
  };
  </script>
  
  <style scoped>
  .datepicker-container {
    display: flex;
    align-items: center;
  }
  
  .primary-datepicker {
    padding: 8px 20px;
    border: 1px solid rgb(200, 200, 200);
    border-radius: 5px;
    font-size: 1rem;
    transition: border-color 200ms ease, background-color 200ms ease;
    background-color: #f9f9f9;
    color: #333;
  }
  
  .primary-datepicker:hover {
    border-color: #999;
  }
  
  .primary-datepicker:focus {
    outline: none;
    border-color: black;
    background-color: #fff;
  }
  </style>
  