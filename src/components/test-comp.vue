<template>
  <div class="card">
    <img alt="Vue logo" src="@/assets/logo.png">
    <div class="info">
      <p class="name">{{ name }}</p>
      <span class="cost">Cost: {{price}} $</span> <br>
      <b v-if="sale" class="text-danger">Skidka</b>
    </div>
    <div class="btn">
      <button v-if="count_product==0" @click="addToCard">Add to card</button>
    </div>
    <div v-if="count_product" class="calc-prod">
      <button @click="calcCount(false)">-</button>
      {{count_product}}
      <button @click="calcCount(true)">+</button>
    </div>
   
  </div>
</template>

<script>

export default {
  name: 'JustComponent',
  props: {
    name:{
      type: String,
      default: 'Name'
    },
    price:{
      type: Number,
      default:1000
    },
    sale:{
      type: Boolean,
      default: false
    }
  },
  data(){
    return {
      count_product: 0
    }
  },
  computed:{
  },
  methods:{
    addToCard(){
      this.count_product = 1
      this.$emit('count',  this.count_product)
    },
    increment(){
      },
    calcCount(isInc){
      if (isInc) {
        this.count_product = this.count_product + 1
      } else if(this.count_product>0){
        this.count_product = this.count_product - 1
      }
      this.$emit('count',  this.count_product)

    },
  }
}
</script>

<style>

</style>