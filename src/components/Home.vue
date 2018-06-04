<template>
    <div>
        <div class="jumbotron">
             <h3 class="display-4">Trade or View your Portfolio</h3>
             <h4 class="lead">You may Save & Load your Data</h4>
             <h4 class="lead">Click on 'End Day' to begin a New Day!</h4>
             <hr class="my-4">
             <p>Your Funds: {{funds | currency}}</p>

         </div>
    </div>
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
