<template>
    <li class="list-item">
        {{ itemData.title }}
        <div>
            <img :src="itemData.pic" class="picture">
        </div>
        <a :href="itemData.link">
            {{ itemData.link }}
        </a>
        <button v-on:click="countCounter">Add me</button>
    </li>
</template>

<script>
    export default {
      props: ['itemData'],
      data: function () {
        return {
          addedToBasket: false
        }
      },
      methods: {
        countCounter: function () {
          if (this.addedToBasket) {
            this.$emit('decrement')
          } else {
            this.$emit('increment')
          }
          this.addedToBasket = !this.addedToBasket
        }
      }
    }
</script>

<style>
    .list-item {
        display: flex;
        flex-direction: column;
        width: 300px;
        margin: 30px 0;
    }
    .picture {
        width: 100px;
        height: 100px;
    }
</style>
