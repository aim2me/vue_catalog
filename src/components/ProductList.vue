<template>
    <div>
        <order-basket :basket="getBasket"></order-basket>
        <product-item
            v-for="item in productList"
            :key="item.id"
            :item-data="item"
            v-on:increment="addProduct(item.id)"
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
            this.basket[id] += 1
          } else {
            this.basket[id] = 1
          }
          // console.log(this.basket)
        },
        delProduct: function (id) {
          if (this.basket.hasOwnProperty(id) && this.basket[id] > 0) {
            this.basket[id] -= 1
          }
          // console.log(this.basket)
        }
      },
      computed: {
        getBasket: function () {
          console.log(this.basket)
          return this.basket
        }
      },
      data () {
        return {
          productList: [
            {
              id: 1,
              title: 'Gretel A7',
              pic: '../assets/Gretel-A7.jpg',
              link: 'https://market.yandex.ru/product/1725613811?show-uid=111646259028863319816001&nid=54726&context=search'
            },
            {
              id: 2,
              title: 'Jinga Simple F315',
              pic: '../assets/Jinga-Simple-F315.jpg',
              link: 'https://market.yandex.ru/product/13623394?show-uid=111646259028863319816002&nid=54726&context=search'
            },
            {
              id: 3,
              title: 'Philips S386',
              pic: '../assets/Philips-S386.jpg',
              link: 'https://market.yandex.ru/product/1729159126?show-uid=111646259028863319816003&nid=54726&context=search'
            }
          ],
          dataCounter: [],
          basket: {}
        }
      }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
