<template>

   <div class="col-sm-6 col-md-4">
         <div class="card">
           <div class="card-header">
                 {{stock.name}} <small>(Price: {{stock.price}})</small>
            </div>
             <div class="card-body">
               <div >
                   <input 
                   type="number"
                   class="form-control"
                   placeholder="Quantity"
                   v-model="quantity"
                   >
               </div>
               
                   <button class="btn btn-primary"
                   @click="buyStock"
                   :disabled="quantity <= 0 "
                   >Buy</button>
               
            </div>
        </div>
   </div>
       


  
</template>
<script>
export default {
    props:['stock'],
    data(){
        return{
            quantity: 0
        }
    },
    methods:{
        buyStock(){
            const order = {
                stockId: this.stock.id,
                stockPrice: this.stock.price,
                quantity: this.quantity
            }
            console.log(order);
            this.$store.dispatch('buyStock', order);
            this.quantity = 0;
            
        },

    }
}
</script>
<style>
.card{
    margin-bottom: 10px;
}
.card-header{
    background-color:#d1ecf1;
}
.btn{
    margin-top: 5px;
}
</style>
