<template>
    <div>
        <SearchJokes v-on:search-text="searchText" />
        <div v-if="this.jokes != ''">
            <Joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke"/>
        </div>
        <div v-else>
            <br>

            <h1>Try again</h1>
            <p>"<strong>{{ text }}</strong>" not found in the server! :( 
            </p>
        </div>
        
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
            jokes:[],
            text:''
            
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
            this.text=text
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