<template>
    <div class="otp-container">
      <input
        v-for="(value, index) in otpArray"
        :key="index"
        :type="isPassword ? 'password' : 'text'"
        :maxlength="1"
        :inputmode="isNumeric ? 'numeric' : 'text'"
        @input="handleInput($event, index)"
        @keydown.backspace="handleBackspace($event, index)"
        class="otp-input"
      />
    </div>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue';
  import { defineProps } from 'vue';
  
  const props = defineProps({
    length: {
      type: Number,
      default: 6, // OTP uzunluğu
    },
    isPassword: {
      type: Boolean,
      default: false, // true: gizli, false: açık karakterler
    },
    isNumeric: {
      type: Boolean,
      default: true, // true: sadece rakamlar, false: karışık karakterler
    },
  });
  
  const otpArray = ref(Array(props.length).fill(''));
  
  const handleInput = (event, index) => {
    const value = event.target.value;
    if ((props.isNumeric && !/^\d$/.test(value)) || value.length > 1) {
      // Sadece tek bir rakam veya uygun karakter kabul edilir
      event.target.value = '';
      return;
    }
    otpArray.value[index] = value;
  
    // İleriye geç
    if (index < props.length - 1 && value !== '') {
      event.target.nextElementSibling?.focus();
    }
  };
  
  const handleBackspace = (event, index) => {
    if (event.key === 'Backspace' && otpArray.value[index] === '' && index > 0) {
      // Geriye geç
      event.target.previousElementSibling?.focus();
    }
  };
  </script>
  
  <style scoped>
  .otp-container {
    display: flex;
    gap: 10px;
  }
  
  .otp-input {
    width: 40px;
    height: 40px;
    text-align: center;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 18px;
    transition: border-color 200ms ease;
    outline: none;
    background-color: #f9f9f9;
  }
  
  .otp-input:focus {
    border-color: black;
  }
  </style>
  