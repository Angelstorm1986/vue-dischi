<template>
  <header>
      <div class="logo">
          <img src="../assets/images/logo-spotify.png" alt="Spotify Logo">
      </div>
  </header>
</template>

<script>
export default {
    name: 'AppHeader',
}
</script>

<style scoped lang="scss">
@import "../style/vars.scss";
@import "../style/general.scss";

header{
    background-color: $bg-disk;
    height: 60px;
    .logo{
        height: 100%;
        display: flex;
        align-items: center;
        img{
            height: 50px;
            padding-left: 50px;
        }
    }
}
</style>