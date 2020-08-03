<template>
 <div>
   <Cards v-bind:products="products" v-on:search-it="SearchResults" />
   <Stationary v-bind:stationaries="stationaries" v-on:search-up="searchAcc" />
   <Footer />
 </div>  
</template>
<script>
import Cards from "./Cards";
import Stationary from "./Stationary";
import Footer from "./layout/Footer";
export default {
  name:"HelloWorld",
  components:{
    Footer,
    Cards,
    Stationary
  },
  data(){
    return{
      products:[
        {
          id:1,
          item:"T-Shirt1",
          rate:"$5",
          img:"../assets/ecom.jpg"
        },
        {
          id:2,
          item:"T-Shirt2",
          rate:"$10",
           img:"../assets/ecom.jpg"

        },
        {
          id:3,
          item:"T-Shirt3",
          rate:"$10",
          img:"../assets/ecom.jpg"

        },
        {
          id:4,
          item:"T-Shirt4",
          rate:"$10",
          img:"../assets/ecom.jpg"

        }
      
      ],
      stationaries:[
        {
          id:1,
          item:"Acc1",
          rate:"$5"
        },
        {
          id:2,
          item:"Acc2",
          rate:"$3"
        },
        {
          id:3,
          item:"Acc3",
          rate:"$5"
        },
        {
          id:4,
          item:"Acc4",
          rate:"$5"
        }
      ]
    }
  },
  methods:{
    SearchResults(searchResult){
      this.products=this.products.filter(product=>product.id==searchResult);
    },
    searchAcc(acc){
      this.stationaries=this.stationaries.filter(stationary=>stationary.id==acc);
    }
  }
  
  
}
</script>
<style scoped>
 
</style>