<template>
  <div class="viewPosts">

  <button type="button" @click="add">Add Component</button>
  <button type="button" @click="addPostsToFrontend">look for the post</button>

<h2>Posts</h2>
  <ul>
    <li v-for="frontEndPost in frontEndPosts" :key ="frontEndPost"  >
      <p>{{frontEndPost.createdOn}}</p>
     <p>{{frontEndPost.postBody}}</p>
    </li>

  </ul>

  </div>
</template>

<script>
import axios from 'axios';
let arrayPosts = [];


export default{

    data () {
      return {
        info: this.info,
        frontEndPosts: [],
      }
    },
  methods: {
      async add() {
       await axios
      .get('https://localhost:5001/api/post')
      //.then(res => console.log(res.data))
      .then((res) => (this.info = res.data))

      //.then((response) => (this.meet = response.data))
      .catch(err => console.log(err))
            //console.log(this.info.postBody);
          for(let i = 0; i <this.info.length; i++)
          {
            arrayPosts.push(this.info[i])

          }
          console.log(arrayPosts);

      },
    addPostsToFrontend()
    {
        this.frontEndPosts = arrayPosts;
        console.log("it works")
    }
  },
};










</script>
<style scoped>
ul {
  list-style-type: none; /* Remove bullets */
}
</style>