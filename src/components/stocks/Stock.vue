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
                   :class="{danger: insufficientFunds}"
                   >
               </div>
               
                   <button class="btn btn-primary"
                   @click="buyStock"
                   :disabled="insufficientFunds || quantity <= 0 "
                   >{{insufficientFunds ? 'insufficient funds' : 'Buy' }}</button>
               
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
    computed: {
        funds(){
            return this.$store.getters.funds;
        },
         insufficientFunds(){
             return this.quantity * this.stock.price > this.funds; 
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
.btn{
    margin-top: 5px;
}
.danger {
    border: 1px solid red;
}
</style>
