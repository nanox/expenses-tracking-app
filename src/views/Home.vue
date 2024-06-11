<template>
    <div class="home">
      <h1>Financial Tracker</h1>
      <AddTransaction @add-transaction="addTransaction" />
      <TransactionList :transactions="transactions" />
      <TransactionChart :transactions="transactions" />
    </div>
  </template>
  
  <script>
  import AddTransaction from '../components/AddTransaction.vue';
  import TransactionList from '../components/TransactionList.vue';
  import TransactionChart from '../components/TransactionChart.vue';
  
  export default {
    components: {
      AddTransaction,
      TransactionList,
      TransactionChart
    },
    data() {
      return {
        transactions: []
      };
    },
    methods: {
      addTransaction(transaction) {
        this.transactions.push(transaction);
      }
    }
  };
  </script>
  