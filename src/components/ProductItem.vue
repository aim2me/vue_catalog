<template>
    <li class="list-item">
        {{ itemData.name }}
        <div>
            <img :src="itemData.pic" class="picture">
        </div>
        <a :href="itemData.link">
            {{ itemData.link }}
        </a>
        <button v-on:click="incCounter">Add me</button>
        <button v-on:click="decCounter">Delete me</button>
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
        incCounter: function () {
          this.$emit('increment')
        },
        decCounter: function () {
          this.$emit('decrement')
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
