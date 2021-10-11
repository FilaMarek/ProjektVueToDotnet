<template>
  <div class="home">
    <div class="app-menu">

    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import SideMenu from "@/components/SideMenu.vue"; // @ is an alias to /src

@Options({
  name: 'Home',
  components: {SideMenu}


  //components: {
  //  SideMenu,
  //},
})
export default class Home extends Vue {}
</script>
