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
  import { defineProps, defineEmits } from 'vue';
  
  const props = defineProps({
    modelValue: {
      type: String,
      default: '', // Tarih değeri
    },
    minDate: {
      type: String,
      default: '', // Seçilebilir minimum tarih
    },
    maxDate: {
      type: String,
      default: '', // Seçilebilir maksimum tarih
    },
    inputStyle: {
      type: String,
      default: '', // Input stil sınıfı
    },
    placeholder: {
      type: String,
      default: 'Select Date', // Placeholder metni
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
  