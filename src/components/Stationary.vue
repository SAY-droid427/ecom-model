<template>
  <div>     
     <div class="sections">
         <h1>Type 2</h1> 
         <hr>       
     </div>
     <div>
       <div class="search">
           <form @submit="Submit">
              <select  v-model='product_type' id="searchbar">
              <option value="1">Acc1</option>
              <option value="2">Acc2</option>
              <option value="3">Acc3</option>
              <option value="4">Acc4</option>
             </select>
                 <button class="btn" type="submit" @click="searchAccessory">Search</button>
           </form>
         </div>
     </div>
    <div class="row">
        <div class="column" v-for="stationary in stationaries" v-bind:key="stationary.id">
            <div class="card">
                <h1>{{stationary.item}}</h1>
                <h2>{{stationary.rate}}</h2>
                <button class="view">View Product</button>
            </div>
        </div>
    </div>  
  </div>    
</template>
<script>
export default {
    name:"Stationary",
    props:['stationaries'],
    data(){
      return{
        product_type:""
      }
    },
    methods:{
      Submit(e){
        e.preventDefault();
        console.log("Testing..");
      },
      searchAccessory(){
        const acc=this.product_type;
        this.$emit('search-up',acc);
        this.product_type="";


      }

    }
    
}
</script>
<style scoped>
* {
  box-sizing: border-box;
}

#searchbar{
  padding:10px 30px;
  margin:20px;
  border:none;
  outline:none;
  background:rgba(255,255,255);
  border-radius:5px;

}
.btn{
  padding:8px 20px;
  color:white;
  background-color: rgba(0,0,0,0.7);
}



.column {
  float: left;
  width: 25%;
  padding: 0 10px;
}

.row {margin: 10px 5px;}

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
  background-color: rgb(255, 250, 250);
}

.sections{
    text-align: left;
    margin:20px;
    margin-top:50px;
    font-family:'montserrat';
}
.card:hover{
    box-shadow:0 8px 20px 0 rgba(0,0,0,0.7);
}
.view{
  border:none;
  outline:none;  
  background-color:rgb(140, 138, 253);
  padding:5px 10px;
  cursor: pointer;
}
.view:hover{
  background-color: rgb(104, 102, 226);
  padding:6px 12px;
}

</style>