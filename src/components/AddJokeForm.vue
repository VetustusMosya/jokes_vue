<template>
  <form @submit.prevent
        class="jokes__box jokes__form">
    <my-input v-model="joke.setup"
              class="jokes__form--input" type="text" placeholder="Input joke">
    </my-input>
    <button @click="addJoke"
            class="jokes__form--button">Add
    </button>
  </form>
</template>

<script>
export default {
  name: 'AddJokeForm',
  data: () => ({
    joke: {
      id:  0,
      setup: '',
    }
  }),
  methods: {
    addJoke(){
      this.joke.id = Date.now() % 10000;
      this.$emit('add', this.joke);
      this.joke = {
        id: 0,
        setup: '',
      }
    },
  }
}
</script>

<style lang="scss" scoped>
.jokes__form{
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
</style>