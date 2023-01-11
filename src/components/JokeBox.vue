<template>
  <div class="jokes__box">
    <p class="jokes__box--text">
      <my-numbering> {{index + 1}}</my-numbering>
      {{ joke.setup }}
    </p>
    <button @click="$emit('remove',joke)" class="jokes__box--delete">❌</button>
  </div>
</template>

<script>
export default {
  name: 'JokeBox',
  props: {
    joke: {
      type: Object,
      required: true,
    },
    index: {
      type: Number,
      required: true,
    }
  }
}
</script>

<style lang="scss" scoped>
  .jokes__box--delete{
    border: none;
    background: transparent;
  }
</style>