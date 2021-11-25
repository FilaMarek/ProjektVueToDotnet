<template>
  <div class="viewPosts">


<div class="header"> <h2>Posts</h2></div>

  <ul>
    <li v-for="frontEndPost in frontEndPosts"  :key ="frontEndPost"  >
      <!--{{frontEndPost.id}} -->
<div class="userPost">
<div class="postHeader"><div class="author"><h4>Autor: {{frontEndPost.authorName}} </h4></div> <div class="postDate"><h5> posted on: {{frontEndPost.createdOn}}</h5></div>
<div class="kudosButton"><h5>Kudos: {{frontEndPost.kudos}}</h5><div class="plusik"><button class="button-3" @click="Kudos(frontEndPost.id, frontEndPost.kudos + 1), frontEndPost.kudos += 1">+</button></div></div>
</div>
<div class="postBody"><p>{{frontEndPost.postBody}}</p></div>
</div>
<div class="spacer"></div>
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

.header
{

  display: grid;
  margin-left: 10%;
  margin-right: 5px;
  border-radius: 5px;
  text-align: center;
}
.postHeader
{
display: grid;
margin-left: 25%;
grid-template-columns: 20% 20% 10%;

}

.kudosButton
{
text-align: left;
margin-left: 20px;
}
.author{
text-align: right;
margin-right: 20px;
}

.postDate
{
margin-right: 0;
text-align: left;
}
.spacer{
  margin-top: 5px;
}
.userPost
{
  background-color: #35495E;
  color:white;
  display: grid;
  margin-left: 10%;
  margin-right: 5px;
  border: 2px solid #41B883;
  border-radius: 5px;
}

.postBody{
  background-color: #41B883;

}

/* CSS */
.button-3 {
  appearance: none;
  background-color: #41B883;
  border: 1px solid rgba(27, 31, 35, .15);
  border-radius: 6px;
  box-shadow: rgba(27, 31, 35, .1) 0 1px 0;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  font-family: -apple-system,system-ui,"Segoe UI",Helvetica,Arial,sans-serif,"Apple Color Emoji","Segoe UI Emoji";
  font-size: 14px;
  font-weight: 600;
  line-height: 20px;
  padding: 6px 16px;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: middle;
  white-space: nowrap;
}

.button-3:focus:not(:focus-visible):not(.focus-visible) {
  box-shadow: none;
  outline: none;
}

.button-3:hover {
  background-color: #41B883;
}

.button-3:focus {
  box-shadow: rgba(46, 164, 79, .4) 0 0 0 3px;
  outline: none;
}

.button-3:disabled {
  background-color: #94d3a2;
  border-color: rgba(27, 31, 35, .1);
  color: rgba(255, 255, 255, .8);
  cursor: default;
}

.button-3:active {
  background-color: #41B883;
  box-shadow: rgba(20, 70, 32, .2) 0 1px 0 inset;
}
</style>
