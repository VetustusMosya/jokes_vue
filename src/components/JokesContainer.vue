<template>
  <h4 class="">Jokes list</h4>
  <joke-box  v-for="(joke, i) in jokes" :joke="joke" :index="i" :key="joke.id"
             @remove="$emit('remove', joke)"
  ></joke-box>
</template>

<script>
import JokeBox from "@/components/JokeBox.vue";
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