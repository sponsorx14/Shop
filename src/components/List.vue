<template>
  <header>
    <div class="container">
      <h1>Welcome to the shop</h1>
      <ListItem></ListItem>
    </div>
  </header>
</template>

<script>
  import ListItem from './ListItem.vue';
  export default {
    name: 'List',
    components: {
      ListItem
    }
  }
</script>

<style lang="scss" scoped>
  .container {
    text-align: center;
    margin: 0 auto;
    max-width: 1200px;
  }
</style>
