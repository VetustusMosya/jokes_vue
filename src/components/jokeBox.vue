<template>
  <div class="jokes__box">
    <p class="jokes__box--text">
      <span>{{ joke.id }} </span> {{ joke.text }}
    </p>
    <button class="jokes__box--delete">❌</button>
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
  }
}
</script>

<style lang="scss" scoped>
  .jokes__box--delete{
    border: none;
    background: transparent;
  }
</style>