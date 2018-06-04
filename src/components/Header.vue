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
    </ul>
    <strong class="navbar-text navbar-right">Funds: {{funds}}</strong>
    <ul class="nav navbar-nav navbar-right">
        <li class="nav-item"><a href="" class="nav-link">End Day</a></li>
        <li class="nav-item dropdown">
        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
          Save & Load
        </a>
        <div class="dropdown-menu" aria-labelledby="navbarDropdown">
          <a class="dropdown-item" href="#">Save Data</a>
          <a class="dropdown-item" href="#">Load Data</a>
        </div>
      </li>
    </ul>

  </div>
</nav>  
</template>
<script>
export default {
      computed: {
              funds(){
                  return this.$store.getters.funds;
              }
          } 
}
</script>
<style>


</style>
