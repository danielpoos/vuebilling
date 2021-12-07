<template>
  <div id="app">
    <h1>Jó reggelt</h1>
    <Billing :rows="rows" @stable="table"/>
  </div>
</template>

<script>
import Billing from './components/Billing.vue'

export default {
  name: 'App',
  components: {
    Billing
  },
  data() {
    return {
      rows: [
        {
          title: 'Kerék',
          price: 100,
          quantity: 12
        },
        {
          title: 'Teleszkóp',
          price: 1000,
          quantity: 300
        },
        {
          title: 'Kormány',
          price: 230,
          quantity: 5
        },
        {
          title: 'Ajtó',
          price: 45120,
          quantity: 321
        },
      ]
    }
  },
  methods:{
    table(e){
      this.rows.maps(function (row){
      if (row.title != e.original.title){
        return row
      }
        row.title = e.new.title
        return row
      })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
