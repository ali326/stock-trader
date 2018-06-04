<template>

   <div class="col-sm-6 col-md-4">
         <div class="card">
           <div class="card-header">
                 {{stock.name}} <small>(Price: {{stock.price}} | Quantity: {{stock.quantity}})</small>
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

                   <button class="btn btn-danger"
                   @click="sellStock"
                   :disabled="quantity <= 0 "
                   >Sell</button>

            </div>
        </div>
   </div>




</template>
<script>
import {mapActions} from 'vuex';
export default {
    props:['stock'],
    data(){
        return{
            quantity: 0
        }
    },
    methods:{
        ...mapActions({
            placeSellOrder: 'sellStock'
        }),
        sellStock(){
            const order = {
                stockId: this.stock.id,
                stockPrice: this.stock.price,
                quantity: this.quantity
            };
            this.placeSellOrder(order);
            this.quantity = 0;
        }

    }
}
</script>
<style>
.card{
    margin-bottom: 10px;
}
.card-header{
    background-color:#f8d7da;
}
.btn{
    margin-top: 5px;
}
</style>
