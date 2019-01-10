<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="stylus">

@font-face
    font-family Exo2-Thin
    font-style normal
    src url(/fonts/Exo2.0-Thin.otf)

@font-face
    font-family TrebuchetMS
    font-style normal
    src url(/fonts/TrebuchetMS.ttf)

*
*:before
*:after
    box-sizing: inherit

body
    background #000 url("/images/bg.jpg") no-repeat center
    background-size cover
    display flex
    justify-content center
    flex-direction column
    min-height 100%
    margin 0


html
    margin 0
    padding 0
    box-sizing border-box
    height 100%
    @media screen and (max-width 860px)
        height auto


</style>
