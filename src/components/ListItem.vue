<template>
  <div class="container">
    <div
      v-for="item in items"
      v-bind:key="item.id"
      class="box"
    >
      <img v-bind:src="item.image" class="box__image" alt="">
      <p
        class="box__name"
      >
        {{ item.name }}
      </p>
      <p
        class="box__details-screen"
      >
        {{ item.details.screen }}
      </p>
      <p
        class="box__details-memory"
      >
        {{ item.details.memory }}
      </p>
      <p
        class="box__details-system"
      >
        {{ item.details.system }}
      </p>
      <p>
        <input
          v-model="basket.qty"
          type="text"
          class="box__input"
          placeholder="Qty"
        >
        of
        {{ item.inStock}}
      </p>
      <button
        @click="addToStore($event)"
      >
        Buy
      </button>
    </div>
  </div>
</template>

<script>
  import data from '../data/index.json';

  export default {
    name: 'ListItem',
    data(){
      return {
        data: data,
        items: [],
        basket: {
          name: '',
          qty: null,
          totalPrice: null
        }
      }
    },
    methods: {
      parseData() {
        data.map(item => {
          this.items.push(item)
        })
      },
      addToStore($event){
        console.log($event.path[1])
        // this.basket.name = $event
      }
    },
    created() {
      this.parseData();
    },
    updated(){
      console.log(this.basket.qty)
    }
  }

</script>

<style lang="scss" scoped>
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    .box{
      border: 2px solid #e6e6e6;
      padding: 20px;
      margin: 20px;
      border-radius: 20px;
      &__image {
        max-width: 200px;
      }
      &__input {
        width: 15%;
      }
    }
  }
</style>
