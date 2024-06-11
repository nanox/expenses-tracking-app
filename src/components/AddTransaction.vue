<template>
    <div class="add-transaction">
      <h2>Add Transaction</h2>
      <form @submit.prevent="addTransaction">
        <div>
          <label for="description">Description:</label>
          <input type="text" v-model="description" required />
        </div>
        <div>
          <label for="amount">Amount:</label>
          <input type="number" v-model="amount" required />
        </div>
        <div>
          <label>
            <input type="radio" value="income" v-model="type" /> Income
          </label>
          <label>
            <input type="radio" value="expense" v-model="type" /> Expense
          </label>
        </div>
        <button type="submit">Add</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        description: '',
        amount: 0,
        type: 'income'
      };
    },
    methods: {
      addTransaction() {
        const transaction = {
          description: this.description,
          amount: parseFloat(this.amount),
          type: this.type,
          date: new Date()
        };
        this.$emit('add-transaction', transaction);
        this.description = '';
        this.amount = 0;
        this.type = 'income';
      }
    }
  };
  </script>
  <style>
  .add-transaction {
    margin-bottom: 20px;
  }
  </style>
  