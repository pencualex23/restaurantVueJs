<template>
  <div>
    <app-header></app-header>
    <router-view></router-view>
    <app-footer></app-footer>
  </div>
</template>

<script>
import Header from './components/header.vue';
import homeBody from './components/homeBody.vue';
import footer from './components/footer.vue';
import reservation from './components/reservation.vue';
export default {
  components:{
    'app-header':Header,
    'app-homeBody':homeBody,
    'app-footer':footer,
    'app-reservation':reservation
  },
  data () {
    return {

    }
  }
}
</script>

<style>
body{
  background-color: #F4F4F4;
  width: 100%;
}

</style>
