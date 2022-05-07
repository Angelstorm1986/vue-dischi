<template>
  <section class="container">
    <div class="disk-container row row-cols-5">
      <div class="col gy-3" v-for="(disk, index) in diskList[0]" :key="index" >
        <app-disk :author="disk.author" :genre="disk.genre" :poster="disk.poster" :title="disk.title" :year="disk.year"/>
      </div>
    </div>
  </section>
</template>

<script>

import axios from 'axios';
import AppDisk from './AppDisk.vue';

export default {
  name: 'AppGrid',
  components: {
    AppDisk
  },
  data(){
    return {
      diskList: []
    }
  },
  mounted() {
    setTimeout(()=>{
      axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((res)=>{
        this.diskList.push(res.data.response);
      }).catch((error) => {
        console.log(error)
      }) 
    },1000)
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
