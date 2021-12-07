<template>
  <div>
    <table>
    <tr><th>Név</th><th>Ár</th><th>Darab</th></tr>
    <BillingRows v-for="row in rows" v-bind:key="row" :row="row" @stable="table"/>
    </table>
  </div>
</template>

<script>
import BillingRows from "./BillingRows"
export default {
  props: ["rows"],
    components:{ BillingRows },
    methods:{
      table(e){
        this.$emit("stable", e);
      }
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
