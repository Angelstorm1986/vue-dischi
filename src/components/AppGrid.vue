<template>
  <section class="container">
    <app-loader v-show="loading"/>
    <div class="disk-container row row-cols-5">
      <div class="col gy-3" v-for="(disk, index) in diskList" :key="index" >
        <app-disk :author="disk.author" :genre="disk.genre" :poster="disk.poster" :title="disk.title" :year="disk.year"/>
      </div>
    </div>
  </section>
</template>

<script>

import axios from 'axios';
import AppLoader from './AppLoader.vue';
import AppDisk from './AppDisk.vue';

export default {
  name: 'AppGrid',
  components: {
    AppLoader,
    AppDisk
  },
  data(){
    return {
      diskList: [],
      loading: false
    }
  },
  mounted() {
    this.loading = true;
    setTimeout(()=>{
      axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((res)=>{
        this.diskList = res.data.response;
        this.loading = false;
      }).catch((error) => {
        this.loading = false;
        console.log(error)
      }) 
    },2000)
  }
}
</script>

<style scoped lang="scss">
@import "../style/vars.scss";
@import "../style/general.scss";

.disk-container{
  margin: 50px 0;
}

</style>
