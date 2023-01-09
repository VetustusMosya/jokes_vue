<template>
  <form @submit.prevent
        class="jokes__box jokes__form">
    <input v-model="joke.text"
           class="jokes__form--input" type="text" placeholder="Input joke">
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
      text: '',
    }
  }),
  methods: {
    addJoke(){
      this.joke.id = Date.now() % 100;
      this.$emit('add', this.joke);
      this.joke = {
        id: 0,
        text: '',
      }
    },
  }
}
</script>

<style lang="scss" scoped>

</style>