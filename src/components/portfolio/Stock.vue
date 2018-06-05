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
                   :class="{danger: insufficientQuantity}"
                   >
               </div>

                   <button class="btn btn-danger"
                   @click="sellStock"
                   :disabled=" insufficientQuantity ||quantity <= 0 "
                   >{{insufficientQuantity ? 'Not Enough Stocks': 'Sell'}}</button>

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
    computed: {
         insufficientQuantity(){
             return this.quantity > this.stock.quantity;
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
    box-shadow: 0 3px 6px rgba(0,0,0,0.16), 0 3px 6px rgba(0,0,0,0.23);
    margin-bottom: 10px;
}
.btn{
    margin-top: 5px;
}
.danger {
    border: 1px solid red;
}
</style>
