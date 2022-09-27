<template>
  <header>
    <div class="logo">
        <img src="https://ajourneyintosound.de/wp-content/uploads/2019/02/spotify_logo.png" alt="logo">
    </div>
  </header>
</template>

<script>
export default {
name : 'HeaderComponent',
}
</script>

<style lang="scss" scoped>
header{
        background-color: hsl(210deg 22% 23%);
        .logo{
            padding: 10px;
        }
        img{
            width: 40px;
        }
    }
</style>