<template>
<main class="content">
        <h1>Ты сегодня покормил кота?</h1>
        <div class="list">
          <div class="item" v-for="product of products">
              <Product :product="product"/>
          </div>
        </div>
</main>
</template>

<script>
// @ is an alias to /src
import Product from '@/components/Product.vue';
import Vue from 'vue';
import vueResource from 'vue-resource'
Vue.use(vueResource);

export default {
    name: 'ProductList',
    components: {
        Product,
    },
    data: () => ({
        products: [
            {
              id: 1,
              taste: "с фуа-гра",
              descr: "Печень утки разварная с артишоками.",
              amount: 10,
              gift: "мышь",
              weight: "0,5",
            },
            {
              id: 2,
              taste: "с рыбой",
              descr: "Головы щучьи с чесноком да свежайшая сёмгушка.",
              amount: 40,
              gift: "2 мыши",
              weight: "2",
            },
            {
              id: 3,
              taste: "с курой",
              descr: "Филе из цыплят с трюфелями в бульоне.",
              amount: 0,
              gift: "5 мышей",
              weight: "5",
              text: "заказчик доволен"
            }
        ],
    }),
};
</script>

<style scoped lang="stylus">


.list
    display flex
    flex-wrap wrap
    flex-direction row
    justify-content space-around
    max-width 1120px
    width 100%
    margin 0 auto
    padding 0 10px

.item
    flex-basis 320px
    margin-bottom 20px
    @media screen and (max-width 1020px)
        flex-basis 32%
    @media screen and (max-width 960px)
        flex-basis 30%
    @media screen and (max-width 860px)
        flex-basis 300px
    @media screen and (max-width 670px)
        flex-basis 320px

h1
    font-family Exo2-Thin, sans-serif
    text-align center
    text-shadow 0 1px 0 #000000
    color #ffffff
    font-size 36px
    font-weight 400

</style>
