<template>
  <div>
    <table>
    <tr><th>Name</th><th>Price</th><th>Quantity</th><th>Operations</th></tr>
    <BillingRows v-for="row in rows" v-bind:key="row" :row="row"/>
    <tr><td><input type="text" v-model="rows.title"></td><td><input type="number" v-model="rows.price"></td><td><input type="number" v-model="rows.quantity"></td><td><button @click="adding">Submit</button></td></tr>
    </table>
  </div>
</template>

<script>
import BillingRows from "./BillingRows"
export default {
  props: ["rows"],
    components:{ BillingRows },
    methods:{
      changing(e){
      this.$emit('changing', e);
    },
      adding(){
        this.$emit('adding', {
          new:{
            title:this.rows.title,
            price:this.rows.price,
            quantity:this.rows.quantity,
          }
        })
        this.rows.title="",
        this.rows.price=null,
        this.rows.quantity=null
      }
    },
    deleting(e){
        this.$emit('deleting', e)
    }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
