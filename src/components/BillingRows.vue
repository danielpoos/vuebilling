<template>
  <tr>
     <td v-if="!unsaved">{{row.title}}</td>
      <td v-if="!unsaved">{{row.price}}</td>
      <td v-if="!unsaved">{{row.quantity}}</td>
      <td v-if="!unsaved"><button @click="editing">Edit</button><button @click="deleting">X</button></td>
      <td v-if="unsaved"><input type="text"></td>
      <td v-if="unsaved"><input type="number"></td>
      <td v-if="unsaved"><input type="number"></td>
      <td v-if="unsaved"><button @click="saving">Save</button></td>
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
      unsaved: false
    }
  },
    methods:{
        editing(){
            this.unsaved = true;
        },
        saving(){
            this.unsaved =false;
            this.$emit('bcha', {
                original: this.row,
                new: {
                    title: this.title,
                    price: this.price,
                    quantity: this.quantity,
                }
            })
        },
        deleting(){
            this.$emit('bdel',{ original: this.row,})
        }
    }
}
</script>
