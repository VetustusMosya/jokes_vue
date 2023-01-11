<template>
  <span>
    <slot></slot>
  </span>
</template>

<script>
export default {
  name: 'my-numbering'
}
</script>

<style lang="scss" scoped>
  span{
    font-weight: bold;
    margin-right: 5px;
    color: #2c3e50;
  }
</style>