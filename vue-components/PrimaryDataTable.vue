<template>
  <div>
    <table class="primary-table">
      <thead class="primary-table-head">
        <th></th>
      </thead>
      <tbody class="primary-table-body">
        <tr>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<style scoped>
html,
body {
  padding: 0;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.primary-table {
  width: 100%;
  border-collapse: collapse;
  margin: 25px 0;
  box-shadow: 0 0 20px rgb(199, 199, 199);
}
.primary-table-head {
  font-size: 1.1em;
  th {
    font-weight: 500;
    background-color: black;

    color: white;
    padding: 10px;
  }
}
.primary-table-body {
  font-size: 1em;
  tr:nth-of-type(even) {
    background-color: rgb(243, 243, 243);
  }

  td {
    padding: 10px 10px;
    text-align: center;
    font-weight: 500;
  }
}
</style>
