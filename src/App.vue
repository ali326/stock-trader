<template>
  <div class="container">
    <app-header></app-header>
    <div class="content">
      <transition name="slide" mode="out-in">
         <router-view />
      </transition>
        
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
   background: #e2e1e0;
   padding: 30px;
 }
 .content{
   margin-top: 20px;
   padding: 15px;
 }
 .slide-enter-active {
      animation: slide-in 200ms ease-out forwards;
 }
 .slide-leave-active {
      animation: slide-out 200ms ease-out forwards;
 }
 @keyframes slide-in {
     from {
        transform: translateY(-30px);
        opacity: 0;
     }
     to {
       transform: translateX(0);
       opacity: 1;
     }
 }
 @keyframes slide-out {
   from {
     transform: translateX(0);
     opacity: 1;
   }
   to {
     transform: translateY(-30px);
     opacity: 0;
   }
 }
</style>
