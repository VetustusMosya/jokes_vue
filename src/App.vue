<template>
  <section class="jokes">
    <div class="container">
      <h1 class="jokes__title">🤡 Bad Jokes</h1>
<!--      <h3 class="jokes__counter">{{ count }}</h3>-->
      <jokes-container :jokes="jokes"
      ></jokes-container>
      <add-joke-form  @add="addJoke"
      ></add-joke-form>
    </div>
  </section>
</template>

<script>
import AddJokeForm from "@/components/AddJokeForm.vue";
import JokesContainer from "@/components/jokesContainer.vue";
export default {
  components: {JokesContainer, AddJokeForm},
  data(){
    return{
      count: 0,
      jokes: [
        {id: 1, text: 'Joke'},
        {id: 2, text: 'Joke'},
      ],
    }
  },
  // created() {
  //   this.count = this.jokes.length;
  // },
  methods:{
    addJoke(joke){
      this.jokes.push(joke);
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
  &__form{
    border-color: #2c3e50;
    &--input{
      border: #42b983 1px solid;
      padding: 3px;
    }
    &--button{
      border: none;
      background-color: #42b983;
      padding: 3px 6px;
      color: white;
    }
  }
}

</style>
