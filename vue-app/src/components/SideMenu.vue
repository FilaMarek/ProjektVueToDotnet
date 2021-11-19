<template>
  <div class="Side-Menu-container">
    <img alt="Vue logo" src="../assets/logo.png" />
    <h1>Post Navigation</h1>
<form @submit.prevent="SubmitForm">


<div class="post-control">
<input v-model="authorName" type="text" placeholder="User Name">
<textarea v-model="postBody" placeholder="Enter your opinion here"></textarea>



</div>
<button>Post</button>

</form>

  </div>
</template>


<script>
import axios from 'axios';

export default{
  data() {
    return {
    postBody: '',
    createdOn: new Date().toISOString(),
    updatedOn: new Date().toISOString(),
    authorName: '',

    };
  },
    methods: {
       SubmitForm() {
        const postCreated =
        {
      createdOn: this.createdOn,
      updatedOn: this.updatedOn,
      postBody: this.postBody,
      authorName: this.authorName,
        };

        if(!this.authorName || !this.postBody)
        {
          alert("Please fill out the user name and your opinion");

        }
        else{

        axios
                .post(
                  'https://localhost:5001/api/post',
                  postCreated
                )
                .then((res) =>
                console.log(res.status));
                     this.createdOn = '';
                     this.updatedOn = '';
                     this.postBody = '';
                     this.authorName = '';
        }
               },
      },
};

</script>


<style scoped lang="scss">
@import "@/scss/global.scss";
.Side-Menu-container {
  background-color: #f7f7f7;
  height: 100vh;
  position:flex;
  flex-direction: column;
  width: $menu-width;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.12), 0 1px 1px rgba(0, 0, 0, 0.24);
  box-sizing: border-box;
}

textarea {
    max-width: 215px;
    min-width: 173px;
    min-height: 30px;
}

input{
 width: 173px;
}


</style>>
