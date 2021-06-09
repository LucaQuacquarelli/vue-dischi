<template>
  <header>
      <div class="logo-container">
          <img :src="logo.logoUrl" :alt="logo.logoAlt">
      </div>
  </header>
</template>

<script>
export default {
    name: "Header",
    data: function() {
        return {
            logo: {
                logoUrl: require("../assets/img/spotify.png"),
                logoAlt: "spotify logo"
            }
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables';
    header {
        background-color: $spotify-bg-theme;
        
        .logo-container {
            padding: 10px;
            padding-top: 14px;
            
            img {
                height: 50px;
            }

        }

    }
</style>