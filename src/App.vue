<template>
  <div id="app">
    <h1>Vue app</h1>
    <Billing :rows="rows" @changing="Changed" @adding="Hozzaad" @deleting="Delete"/>
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
    changing(e){
    this.rows.map(function (r) {
        if (r.title != e.original.title) {
          return r
        }
        r.title = e.new.title
        return r
      })
    },
    adding(e){
      this.rows.push(e.new)
    },
    deleting(e){
      this.rows.splice(this.rows.indexOf(e.new));
    },
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
