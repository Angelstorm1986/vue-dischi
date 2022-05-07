<template>
    <div class="disk-card">
        <img :src="poster" :alt="title">
        <h4>{{title}}</h4>
        <p>{{author}}</p>
        <p>{{year}}</p>
    </div>
</template>

<script>
export default {
    name:'AppDisk',
    props:{
        author: String,
        genre: String,
        poster: String,
        title: String,
        year: String
    }
}
</script>

<style scoped lang="scss">
@import "../style/vars.scss";
@import "../style/general.scss";

.disk-card{
    background-color: $bg-disk;
    height: 100%;
    text-align: center;
    padding: 20px;
    img{
        width: 100%;
        max-height: 150px;
        min-height: 150px;
    }
    h4{
        margin-top: 20px;
        color: $color-text-title;
    }
    p{
        color: $color-text-subtitle;
    }
}

</style>