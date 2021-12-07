<template>
  <tr>
      <td>{{row.title}}</td>
      <td>{{row.price}}</td>
      <td>{{row.quantity}}</td>
  </tr>
</template>

<script>
export default {
  props: ["row"],
    data() {
    return {
      title:this.row.title,
      price:this.row.price,
      quantity:this.row.quantity,
    }
  },
    methods:{
      table(e){
        this.$emit("stable", e);
      }
    }
}
</script>
