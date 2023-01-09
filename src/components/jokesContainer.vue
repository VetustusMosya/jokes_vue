<template>
  <h4 class="">Jokes list</h4>
  <joke-box  v-for="joke in jokes" :joke="joke"
  ></joke-box>
</template>

<script>
import JokeBox from "@/components/jokeBox.vue";
export default {
  name: 'JokesContainer',
  components: {JokeBox},
  props: {
    jokes:{
      type: Array,
      required: true, //обязательный
    }
  },
}
</script>

<style lang="scss" scoped>

</style>