<template>
  <div class="container">
    <app-header></app-header>
    <div class="content">
        <router-view />
    </div>
      
                
      
    

  </div>
</template>

<script>
import Header from './components/Header'
export default {
  components:{
    appHeader: Header
  },
  created(){
    this.$store.dispatch('initStocks')
  }
}
</script>

<style>
 body {
   padding: 30px;
 }
 .content{
   padding: 15px;
 }
</style>
