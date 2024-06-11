<template>
    <div>
      <h2>Expenses Chart</h2>
      <BarChart :chart-data="chartData" />
    </div>
  </template>
  
  <script>
  import { Bar } from 'vue-chartjs/legacy';
  import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js';
  ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);
  
  export default {
    components: {
      BarChart: {
        extends: Bar,
        props: ['chartData'],
        mounted() {
          this.renderChart(this.chartData, { responsive: true, maintainAspectRatio: false });
        }
      }
    },
    props: ['transactions'],
    computed: {
      chartData() {
        const expenses = this.transactions.filter(t => t.type === 'expense');
        const dates = [...new Set(expenses.map(e => e.date.toLocaleDateString()))];
        const data = dates.map(date => {
          return expenses.filter(e => e.date.toLocaleDateString() === date).reduce((acc, cur) => acc + cur.amount, 0);
        });
  
        return {
          labels: dates,
          datasets: [
            {
              label: 'Expenses',
              backgroundColor: '#f87979',
              data
            }
          ]
        };
      }
    }
  };
  </script>
  