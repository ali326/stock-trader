<template>
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <router-link to="/" class="navbar-brand">Stock Trader</router-link>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarContent">
    <ul class="navbar-nav mr-auto">
      <li class="nav-item">
        <router-link to="/portfolio" class="nav-link"><a>Portfolio</a></router-link>
      </li>
      <li class="nav-item">
        <router-link to="/stocks" class="nav-link"><a>Stocks</a></router-link>
      </li>
         <li class="nav-item dropdown" 
         >
        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
          Save & Load
        </a>
        <div class="dropdown-menu" aria-labelledby="navbarDropdown">
          <a class="dropdown-item"  @click="saveData" href="#">Save Data</a>
          <a class="dropdown-item" @click="loadData" href="#">Load Data</a>
        </div>
      </li>
      <li class="nav-item my-2 my-lg-0">
        <a class="nav-link navbar-right" @click="endDay" href="#">End Day</a>
      </li>
    </ul>
    <strong class="navbar-text navbar-right">Funds: {{funds | currency}}</strong>

  </div>
</nav>  
</template>
<script>
import {mapActions} from 'vuex'

export default {
      data(){
        return{
          isDropDownOpen: false
        }
        
      },
      computed: {
              funds(){
                  return this.$store.getters.funds;
              }
          },
          methods: {
            ...mapActions({
              randomizeStocks: 'randomizeStocks',
              fetchData: 'loadData'
            }),
            endDay(){
              return this.randomizeStocks();
            },
            saveData(){
              const data = {
                funds: this.$store.getters.funds,
                stockPortfolio: this.$store.getters.stockPortfolio,
                stocks: this.$store.getters.stocks
              }
              this.$http.put('data.json', data);
            },
            loadData(){
                this.fetchData();
            }
          } 
}
</script>
<style>


</style>
