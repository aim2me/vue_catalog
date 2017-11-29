<template>
    <div>
        <order-basket :basket="getBasket"></order-basket>
        <product-item
            v-for="item in productList"
            :key="item.id"
            :item-data="item"
            v-on:increment="addProduct(item.id, item.name)"
            v-on:decrement="delProduct(item.id)"
        ></product-item>
    </div>
</template>

<script>
    import ProductItem from './ProductItem'
    import OrderBasket from './OrderBasket'

    export default {
      name: 'ProductList',
      components: {
        ProductItem,
        OrderBasket
      },
      methods: {
        addProduct: function (id) {
          if (this.basket.hasOwnProperty(id)) {
            // vue component has $set method
            console.log(id)
            this.$set(this.basket, id, this.basket[id] + 1)
          } else {
            this.$set(this.basket, id, 1)
          }
        },
        delProduct: function (id) {
          if (this.basket.hasOwnProperty(id) && this.basket[id] > 0) {
            this.$set(this.basket, id, this.basket[id] - 1)
          }
        }
      },
      computed: {
        getBasket: function () {
          return this.productList[1]
        }
      },
      data: function () {
        return {
          productList: [
            {
              id: 1,
              name: 'Gretel A7',
              pic: '../assets/Gretel-A7.jpg',
              link: 'https://market.yandex.ru/product/1725613811?show-uid=111646259028863319816001&nid=54726&context=search'
            },
            {
              id: 2,
              name: 'Jinga Simple F315',
              pic: '../assets/Jinga-Simple-F315.jpg',
              link: 'https://market.yandex.ru/product/13623394?show-uid=111646259028863319816002&nid=54726&context=search'
            },
            {
              id: 3,
              name: 'Philips S386',
              pic: '../assets/Philips-S386.jpg',
              link: 'https://market.yandex.ru/product/1729159126?show-uid=111646259028863319816003&nid=54726&context=search'
            }
          ],
          basket: {}
        }
      }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
