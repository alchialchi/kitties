<template>
  <div>
    <div class="active"
         :class="{
           'active unavailable': product.amount === 0,
           'selected': product.selected,
         }"
         @click="choose"
    >
      <div class="descr">Сказочное заморское яство</div>
      <div class="name">Нямушка</div>
      <div class="taste">{{ product.taste }}</div>
      <div class="amount">{{ product.amount }} порций</div>
      <div class="gift">{{ product.gift }} в подарок</div>
      <div class="weight">{{ product.weight }} <span class="weight__kg">кг</span></div>
      <div class="text">{{ product.text }}</div>
    </div>
      <p class="lalka" v-if="product.selected">{{ product.descr }}</p>
      <p v-else-if="product.amount > 0">Чего сидишь? Порадуй котэ, <a href="#" @click="choose" >купи.</a></p>
      <p v-else class="none">Печалька, {{ product.taste }} закончился.</p>

  </div>
</template>

<script>
  export default {
      name: 'Product',
      props: ['product'],
      methods: {
          choose () {
            if (this.product.amount > 0) {
                this.$set(this.product, "selected", !this.product.selected)
              }
          }
      }
  };
</script>

<style scoped lang="stylus">

.active
    height 480px
    border 4px solid #1698d9
    border-radius 20px
    background #f2f2f2 url("/images/cat.png") no-repeat left bottom
    clip-path polygon(45px 0, 100% 0, 100% 100%, 0 100%, 0 45px) // заменить на svg чтоб ie схавал
    position relative
    padding 20px 45px 15px
    @media screen and (max-width 960px)
        padding 20px 30px 15px
    &:before
        position absolute
        content ''
        top 22px
        left -22px
        width 75px
        height 4px
        background-color #1698d9
        transform rotate(-45deg)
        z-index 3

.unavailable
    border 4px solid #b3b3b3
    &:before
        background-color #b3b3b3
    &:after
        position absolute
        left 0
        right 0
        top 0
        bottom 0
        background rgba(255,255,255,0.5)
        content ''
        z-index 0
        display block
        border-radius 20px

.selected
    border 4px solid #e62e7a
    &:before
        position absolute
        content ''
        top 22px
        left -22px
        width 75px
        height 4px
        background-color #e62e7a
        transform rotate(-45deg)
        z-index 3

p
    color #ffffff
    text-shadow 0 1px 0 #000000
    font-family TrebuchetMS
    font-size 13px
    font-weight 400
    line-height 16px
    text-align center
    @media screen and (max-width 670px)
        font-size 16px
a
  color #1698d9
  font-weight 700
  border-bottom 1px dashed #1698d9
  text-decoration none

.none
    color #ffff66

.name
    font-family TrebuchetMS
    font-size 48px
    color #000000
    font-weight 700

.taste
    color #000000
    font-family TrebuchetMS
    font-size 24px
    font-weight 700
    margin-bottom 15px

.descr
.amount
.gift
.text
    color #666666
    font-family: TrebuchetMS
    font-size 14px
    font-weight 400
    line-height 16px

.descr
    margin-bottom 5px
    font-size 16px

.weight
    position absolute
    bottom 15px
    right 10px
    background-color #1698d9
    border-radius 50%
    width 80px
    height 80px
    padding-top 20px
    color #ffffff
    font-family TrebuchetMS
    font-size 42px
    font-weight 400
    line-height 22px
    text-align center
    &__kg
        font-size 21px
        display block
        margin-top 10px

.unavailable .weight
    background-color #b3b3b3

.selected .weight
    background-color #e62e7a


</style>
