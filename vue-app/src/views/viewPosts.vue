<template>
  <div class="viewPosts">

  <button type="button" @click="add">Add Component</button>



  </div>
</template>

<script>
import axios from 'axios';
let arrayMeeting = [];


export default{

    data () {
      return {
        info: this.info,
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
            arrayMeeting.push(this.info[i].postBody)

          }
          console.log(arrayMeeting);
      },
  },
};










</script>
