<template>
    <div>
        <SearchJokes v-on:search-text="searchText" />
        <Joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke"/>
    </div>
</template>

<script>
import axios from "axios";
import Joke from '../../components/jokes';
import SearchJokes from '../../components/searchJokes';
export default {
    components:{
        Joke,
        SearchJokes
    },
    data(){
        return{
            jokes:[]
        }
    },
    async created(){
        const config={
            headers:{
                'Accept':'application/json'
            }
        }
        try {
             const res = await axios.get('https://icanhazdadjoke.com/search',config)
            this.jokes=res.data.results
            //console.log(this.jokes)
        } catch (error) {
            console.log(error)
        }
       
    },
    methods: {
       async searchText(text){
           const config={
            headers:{
                'Accept':'application/json'
            }
        }
        try {
             const res = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`,config)
            this.jokes=res.data.results
            //console.log(this.jokes)
        } catch (error) {
            console.log(error)
        }
        }
    },
    head(){
        return{
            title:"Dad jokes",
            meta:[
                {
                    hid:"description",
                    name:"description",
                    content:"Best Place for Corny Dad Jokes"
                }
            ]
        }
    }
}
</script>
<style >
    a{
        text-decoration: none;
    }
</style>