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
    default: 'text', // Default input type is text, can be changed to email, password, etc.
  },
  modelValue: {
    type: String,
    default: '', // Two-way binding value
  },
  placeholder: {
    type: String,
    default: 'Enter value', // Default placeholder, can be customized
  },
  inputStyle: {
    type: String,
    default: '', // Additional class names can be added here
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
