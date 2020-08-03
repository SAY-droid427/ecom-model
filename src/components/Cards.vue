<template>
  <div> 
     
     <div class="all">
       <select class="search-it-all" v-model="type">
         <option value="Type1">Type 1</option>
         <option value="Type2">Type 2</option>
         <option value="Type3">Type 3</option>
       </select>
       <button type="submit" class="btn"  @click="findType">Search Product</button>
     </div>
     
     <div class="sections">        
         <h1>Type1</h1> 
         <hr>       
        
     </div> 
     <div>
       <div class="search">
       <form @submit="Submit">
         <select  v-model='product_type' class="searchbar">
         <option value="1">T-Shirt1</option>
         <option value="2">T-Shirt2</option>
         <option value="3">T-Shirt3</option>
         <option value="4">T-Shirt4</option>
         </select>
         <button class="btn" type="submit"  @click="searchProduct">Search</button>
       </form>
        </div>
     </div>  
    <div class="row">
        <div class="column" v-for="product in products" v-bind:key="product.id">
            <div class="card">   
                <h1>{{product.item}}</h1>
                <h2>{{product.rate}}</h2>
                <button class="view">View Product</button>
            </div>
        </div>
    </div>      
  </div>    
</template>
<script>
export default {
    name:"Cards",
    props:['products'] ,
    data(){
      return{
        product_type:"",
        type:""
      }
    },
    methods:{
      Submit(e){
        e.preventDefault();
        console.log("Testing...");
      },
      searchProduct(){
        console.log(this.product_type);
        const searchResult=this.product_type;
        this.$emit('search-it',searchResult);     
        this.product_type="";   
      },
      findType(){
        console.log(this.type);
      }
    }  
    
}
</script>
<style scoped>
 * {
  box-sizing: border-box;
}

body {
  font-family: Arial, Helvetica, sans-serif;
}

.column {
  float: left;
  width: 25%;
  padding: 0 10px;
}

.row {
  margin: 10px 5px;
  
  }

.row:after {
  content: "";
  display: table;
  clear: both;
}

@media screen and (max-width: 600px) {
  .column {
    width: 100%;
    display: block;
    margin-bottom: 20px;
  }
}

.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  padding: 16px;
  text-align: center;
  background-color: rgb(255, 251, 251);
}
.heading{
    background-image: url("../assets/wallpaper2.png");
    background-size: contain;    
    margin:100px 0;
    width:100%;
    height:300px;
    color:white;
}
.cover{
    height:300px;
    width:80%;
    margin:0 auto;
    background-color: rgba(0,0,0,0.7);
    text-align: center;
}
.head{
    padding-top:100px;
}
.sections{
    text-align: left;
    margin:20px;
    font-family:'montserrat';
}
.card:hover{
    box-shadow:0 8px 20px 0 rgba(0,0,0,0.7);
}

.searchbar{
  margin:10px;
  padding:10px 30px;
  border:none;
  outline:none;
  background:rgba(255,255,255);
  border-radius:5px;


}
.btn{
  padding:8px 20px;
  background-color: rgba(0,0,0,0.7);
  color:white; 
}
.view{
  border:none;
  outline:none;  
  background-color:rgb(140, 138, 253);
  padding:5px 10px;
  cursor:pointer;
}
.view:hover{
  background-color: rgb(104, 102, 226);
  padding:6px 12px;
}
.all{
  margin:20px;
}
.search-it-all{
  margin-left:10px;
  padding:10px 10px;
  width:40%;
  border:none;
  outline:none;
  background:rgb(255,255,255);
  border-radius: 0 8px;
  transition:0.4s;
  box-shadow:0px 0px 5px 0px rgba(0,0,0,0.7);
}
.search-it-all:focus{
  border-radius:8px 0;
}

</style>