<template>
    <div class="logo-wrap">
        <img id="logo" :src="this.imgUrl">
    </div>
</template>

<script>
export default {
  name: 'Logo',
  data: function() {
    return {
        imgUrl: 'https://proxy.duckduckgo.com/iu/?u=http%3A%2F%2Fwww.yearoftheyes.com%2Fwp-content%2Fuploads%2F2016%2F12%2FSocial-Media-Icons-Pink-Transparent-02.png&f=1'
    }
  },
}
</script>


<style lang="sass" scoped>

#logo
    width: 200px
    height: 200px
    transition: all 300ms ease-in-out
    position: relative

    &:after
        content: ''
        position: absolute
        top: 50%
        left: 50%
        color: red
        z-index: 100
        font-size: 2rem

    &:hover
        filter: blur(2px)
        transform: scale(0.8)


</style>
