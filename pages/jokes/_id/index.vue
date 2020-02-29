<template>
    <div>
        <nuxt-link to="/jokes">Back to jokes</nuxt-link>
        <br>
        <h1>{{ joke.joke }}</h1>
        <br>
        <hr>
        <small>id: {{joke.id}}</small>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    data(){
        return{
            joke:{}
        }
    },
    async created() {
      const config ={
          headers:{
              Accept:"application/json"
          }
      }
      try {
          const res = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`,config)
        this.joke=res.data

      } catch (error) {
          console.log(error)
      }  
    },
}
</script>