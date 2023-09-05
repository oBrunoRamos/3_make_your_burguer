<template>
  <BurguerBanner/>
  <div class="main-container">
    <h1>Monte o seu Burguer:</h1>
    <BurguerForm/>
  </div>
</template>

<script>
  import BurguerBanner from '../components/Banner.vue';
  import BurguerForm from '../components/BurguerForm.vue'

  export default {
    name: 'Home',
    components:{
      BurguerBanner,
      BurguerForm
    }
  }

</script>
