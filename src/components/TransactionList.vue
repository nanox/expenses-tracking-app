<template>
    <div class="transaction-list">
      <h2>Transaction List</h2>
      <ul>
        <li v-for="transaction in transactions" :key="transaction.date">
          {{ transaction.description }} - {{ transaction.amount }} - {{ transaction.type }} - {{ transaction.date.toLocaleDateString() }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    props: ['transactions']
  };
  </script>
  