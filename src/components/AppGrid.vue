<template>
  <section class="container">
    <app-loader v-show="loading"/>
    <app-search @performSearch="mySearch" :diskAll="diskList" :diskGenres="genre"/>
    <div class="disk-container row row-cols-5">
      <div class="col gy-3" v-for="(disk, index) in filteredList" :key="index" >
        <app-disk :author="disk.author" :genre="disk.genre" :poster="disk.poster" :title="disk.title" :year="disk.year"/>
      </div>
    </div>
  </section>
</template>

<script>

import axios from 'axios';
import AppSearch from './AppSearch.vue';
import AppLoader from './AppLoader.vue';
import AppDisk from './AppDisk.vue';

export default {
  name: 'AppGrid',
  components: {
    AppSearch,
    AppLoader,
    AppDisk
  },
  data(){
    return {
      diskList: [],
      loading: false,
      searchText: '',
      genre: []
    }
  },
  methods:{
    mySearch(text){
      this.searchText = text;
    }  
  },
  computed:{
    filteredList(){
      if(this.searchText === '') {
        return this.diskList
      }else {
        return this.diskList.filter((el) => el.genre === this.searchText)
      }
    }
  },
  mounted() {
    this.loading = true;
    setTimeout(()=>{
      axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((res)=>{
        console.log(res)
        this.diskList = res.data.response;
        this.diskList.forEach((el) => {
          if(!this.genre.includes(el.genre)) {
            this.genre.push(el.genre)
          }
        })
        console.log(this.genre)
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
