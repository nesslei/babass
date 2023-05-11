<template>
    <Bar
      id="my-chart-id"
      :options="chartOptions"
      :data="chartData"
    />
  </template>

  <script>
  import { Bar } from 'vue-chartjs'
  import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
  
  ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
  
  export default {
    name: 'BarChart',
    components: { Bar },
    data() {
      return {
        year: '',
        maternal: '',
        mortality: '',
        neonatal: '',
        postneonatal: '',
        deaths: '',
        
        chartData: {
            labels: ["deaths"],
        datasets: [
          {
            label: 'maternal',
            backgroundColor: ['#483c34','#614f45'],
            hoverBackgroundColor: '#5555',
            data: [this.year, this.maternal, this.mortality, this.neonatal, this.postneonatal],
            
          }
        ]
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: { 
      legend: {
        labels: {
          color: "#483c34", 
          font: {
            size: '18' ,
            family: 'Bevan',
          }
        }
      }
    }
    }
    }
    },

    mounted() {
      this.fetchData()
    }, 
    methods: {
      async fetchData() {
          try {
            const response = await fetch('https://data.cityofnewyork.us/resource/fcau-jc6k.json')
            const data = await response.json()
            const randomIndexOne = Math.floor(Math.random() * data.length)

            this.year = data[randomIndexOne].year
            this.maternal = data[randomIndexOne].maternal
            this.mortality = data[randomIndexOne].mortality
            this.neonatal = data[randomIndexOne].neonatal
            this.postneonatal = data[randomIndexOne].postneonatal

          } catch (error) {
            console.log(error)
          }
        }
      }
    }
</script>
