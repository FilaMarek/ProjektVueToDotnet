<template>
  <div class="Side-Menu-container">
    <img alt="Vue logo" src="../assets/logo.png" />

  </div>
</template>


<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({

name:'SideMenu',
components: {}
})

export default class SideMenu extends Vue { }
</script>


<style scoped lang="scss">
@import "@/scss/global.scss";
.Side-Menu-container {
  background-color: #f7f7f7;
  height: 100vh;
  width: $menu-width;
  display: flex;
  flex-direction: column;
  padding: 0.8rem;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.12), 0 1px 1px rgba(0, 0, 0, 0.24);
  box-sizing: border-box;
}

</style>>
