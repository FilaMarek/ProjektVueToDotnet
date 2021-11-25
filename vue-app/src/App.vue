<template>
<div class="app">
  <div class="app-menu">
  <side-menu/>
  </div>
    <div id="nav">
    <router-link to="/">Home</router-link>
  </div>
  <router-view />

</div>

</template>


<script lang="ts">
import { Options, Vue } from "vue-class-component";
import SideMenu from "@/components/SideMenu.vue";


@Options({
  name: 'viewPosts',
  components: {SideMenu},
})
export default class Home extends Vue {
}
</script>





<style lang="scss">

@import "@/scss/global.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  .app-menu{
    position: fixed;
  }
  .app-content{
    padding: 1.2rem;
    width: 90%;
    margin: 1rem auto 1rem $menu-width;
    text-align: left;
  }

}


#nav {
  margin-left: 250px;
  text-align: left;
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
