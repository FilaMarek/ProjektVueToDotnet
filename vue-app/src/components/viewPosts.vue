<template>
  <div class="viewPosts">



  <h2>Posts</h2>
  <ul>
    <li v-for="frontEndPost in frontEndPosts"  :key ="frontEndPost"  >
      <!--{{frontEndPost.id}} -->
      <p>Autor: {{frontEndPost.authorName}} |   posted on: {{frontEndPost.createdOn}}</p>
     <h4>{{frontEndPost.postBody}}</h4>
     <p>Kudos: {{frontEndPost.kudos}} <button @click="Kudos(frontEndPost.id, frontEndPost.kudos + 1), frontEndPost.kudos += 1">+</button></p>
    </li>

  </ul>

  </div>
</template>

<script>
import axios from 'axios';
let arrayPosts = [];

export default{

created ()
{
  this.add();
},

    data () {
      return {
        id: '',
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
      .catch(err => console.log(err))
           // console.log(this.info);
          this.info.sort((a, b) => parseFloat(b.id) - parseFloat(a.id))
          for(let i = 0; i <this.info.length; i++)
          {
            arrayPosts.push(this.info[i]);
          }
        this.frontEndPosts = arrayPosts;
      arrayPosts = [];

      },

       Kudos(id)
       {



          const postLiked = {
          id : id
        };
        axios
                .post(
                  'https://localhost:5001/api/kudos',
                  postLiked
                )
                .then((res) =>
                console.log(res.status));
       },




  },

};










</script>


<style scoped>
ul {
  list-style-type: none; /* Remove bullets */
}
</style>