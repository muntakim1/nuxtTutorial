<template>
    <div>
        <h1>About DadJokes</h1>
        <p>This is an app that displays corny dad jokes</p>
        <br>

        <b-card>
            <b-card-title> Build with NuxtJS</b-card-title>
            <b-card-sub-title>Muntakimur Rahaman</b-card-sub-title>
        </b-card>
        <br>
        <br>
        <small>*This web app is an example web app following by traversy media</small>
    
    </div>
</template>


<script>
export default {
    head(){
        return{
            title: 'About the App',
            meta:[
                {
                    hid:"description",
                    name: "description",
                    content: "Best place for corny dad jokes"
                }
            ]
        }
    }
}
</script>   