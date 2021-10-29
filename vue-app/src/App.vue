<template>
<div class="app">
    <div id="nav">
    <router-link to="/">Home</router-link> |
  </div>
  <router-view />
<side-menu/>
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
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
