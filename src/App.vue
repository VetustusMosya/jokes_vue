<template>
  <section class="jokes">
    <div class="container">
      <h1 class="jokes__title">🤡 Bad Jokes</h1>
<!--      <h3 class="jokes__counter">{{ count }}</h3>-->
      <jokes-container v-if="jokes.length !== 0"
          :jokes="jokes" @remove="removeJoke"
      ></jokes-container>
      <h4 v-else>Empty jokes list</h4>
      <add-joke-form  @add="addJoke"
      ></add-joke-form>
    </div>
    <button @click="fetchJokes">fetch</button>
  </section>
</template>

<script>
import axios from 'axios';
import AddJokeForm from "@/components/AddJokeForm.vue";
import JokesContainer from "@/components/JokesContainer.vue";
export default {
  components: {JokesContainer, AddJokeForm},
  data(){
    return{
      count: 0,
      jokes: [
        {
          "error": false,
          "category": "Pun",
          "type": "twopart",
          "setup": "I was feeling depressed, my wife put her hand on my back and said \"Earth.\"",
          "delivery": "It meant the world to me.",
          "flags": {
            "nsfw": false,
            "religious": false,
            "political": false,
            "racist": false,
            "sexist": false,
            "explicit": false
          },
          "safe": true,
          "id": 282,
          "lang": "en"
        },
        {
          "error": false,
          "category": "Pun",
          "type": "twopart",
          "setup": "What did the fish say when it swam into the wall?",
          "delivery": "Dam.",
          "flags": {
            "nsfw": false,
            "religious": false,
            "political": false,
            "racist": false,
            "sexist": false,
            "explicit": true
          },
          "id": 205,
          "safe": false,
          "lang": "en"
        },
        // {
        //   "error": false,
        //   "category": "Dark",
        //   "type": "single",
        //   "joke": "Hey girl are you a school? Because I want to shoot some kids up inside of you.",
        //   "flags": {
        //     "nsfw": true,
        //     "religious": false,
        //     "political": false,
        //     "racist": false,
        //     "sexist": false,
        //     "explicit": true
        //   },
        //   "safe": false,
        //   "id": 269,
        //   "lang": "en"
        // },
      ],
    }
  },
  // created() {
  //   this.count = this.jokes.length;
  // },
  methods:{
    addJoke(joke){
      this.jokes.push(joke);
    },
    removeJoke(joke){
      this.jokes = this.jokes.filter(j => j.id !== joke.id);
    },
    async fetchJokes(){
      try{
        const response = await axios.get('https://v2.jokeapi.dev/joke/Any',
            {params: {
                'Content-Type': 'application/json',
                lang: 'uk',
              }});
        console.log(response.data);
        // localStorage.setItem('joke', JSON.stringify(response));
      } catch(e) {
        console.log(e);
      }
    }
  }
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.container{
  max-width: 1440px;
  width: 100%;
  margin: 0 auto;
}

.jokes{
  .container{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  &__box{
    max-width: 300px;
    width: 100%;
    border: #42b983 3px solid;
    margin: 5px;
    padding: 5px ;
    display: flex;
    justify-content: space-between;
  }
}

</style>
