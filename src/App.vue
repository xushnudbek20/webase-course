<template>
  <div id="app">
    <h1>
      Webase Market
    </h1>
    <div class="cards">
      <TestComponents 
        v-for="(product, index) in products" 
        :key="index"
        :name="product.name"
        :price="product.price"
        :sale="product.sale"
        @count="productCount($event, index)"
       />
    </div>
     <div v-if="products_card.length" class="product-card">
      <div v-for="(product,index) in products_card" :key="index" class="cardd">
          <p>Mahsulot: {{product.name}}</p>
          <p>Soni: {{product.count}}</p>
          <p>Narxi: {{product.price*product.count}}</p>
          <hr>
      </div>
      <b>Umumiy summa: </b>{{getTotalSum()}}
    </div>
  </div>
</template>

<script>
import TestComponents from "./components/test-comp.vue";

export default {
  name: 'App',
  components: {
    TestComponents
  },
  data(){
    return {
      products:[
        { name:"Iphone 14 pro Max", price:1500, count: 0, sale:true},
        { name:"Iphone 13 pro Max", price:1300, count: 0, sale:true},
        { name:"Iphone 12 pro Max", price:1200, count: 0, sale:true},
        { name:"Tv Smart", price:200, count: 0, sale:false},
      ],
      products_card:[],
      totalSum: 0
    }
  },
  methods:{
    productCount(count, index){
      this.products[index].count = count
      if (!this.products_card.find(el=>el.name==this.products[index].name)) {
        this.products_card.push(this.products[index])
      }
    },
    getTotalSum(){
      let totalSum = 0
      this.products_card.forEach(el => {
        totalSum += el.price*el.count
      })
      return totalSum
    }
  }
}
</script>

<style>
@import url('./assets/styles.css');
</style>
