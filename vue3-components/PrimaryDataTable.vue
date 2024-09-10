<template>
  <div>
    <table class="primary-table">
      <thead class="primary-table-head">
        <tr>
          <!-- Başlıkları dinamik olarak oluştur -->
          <th v-for="(header, index) in headers" :key="index">{{ header }}</th>
        </tr>
      </thead>
      <tbody class="primary-table-body">
        <tr v-for="(row, rowIndex) in rows" :key="rowIndex">
          <!-- Her satırdaki hücreleri dinamik olarak oluştur -->
          <td v-for="(cell, cellIndex) in row" :key="cellIndex">{{ cell }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

// Props tanımla: headers ve rows
const props = defineProps({
  headers: {
    type: Array,
    required: true,
  },
  rows: {
    type: Array,
    required: true,
  },
});
</script>

<style scoped>
.primary-table {
  width: 100%;
  border-collapse: collapse;
  margin: 25px 0;
  box-shadow: 0 0 20px rgb(199, 199, 199);
}

.primary-table-head {
  font-size: 1.1em;
}

.primary-table-head th {
  font-weight: 500;
  background-color: black;
  color: white;
  padding: 10px;
}

.primary-table-body {
  font-size: 1em;
}

.primary-table-body tr:nth-of-type(even) {
  background-color: rgb(243, 243, 243);
}

.primary-table-body td {
  padding: 10px 10px;
  text-align: center;
  font-weight: 500;
}
</style>
