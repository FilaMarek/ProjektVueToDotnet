<template>
  <div class="Side-Menu-container">
    <img alt="Vue logo" src="../assets/logo.png" />
    <h1>Post Navigation</h1>
<form @submit.prevent="SubmitForm">


<div class="post-control">

<textarea v-model="postMessage" placeholder="Enter your opinion here"></textarea>



</div>
<button>Post</button>

</form>

  </div>
</template>


<script>

export default{
  data(){
    return {
      postMessage: '',

    };
  },
    methods: {
      SubmitForm() {
        console.log("post " + this.postMessage);
        this.postMessage = '';
      },
    },
};

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

textarea {
    max-width: 215px;
}


</style>>
