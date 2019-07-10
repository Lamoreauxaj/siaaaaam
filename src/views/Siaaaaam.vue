<template>
  <v-flex class="siaaaaam">
    <h1 class="display-3">There are {{ correct }} A's in...</h1>
    <div class="marquee-container">
      <div class="marquee">SI<span :key="n" v-for="n in Number(correct)">A</span>M</div>
    </div>
  </v-flex>
</template>

<script>
export default {
  name: 'Siaaaaam',
  data() {
    return {
      correct: String(Math.floor((new Date() - new Date(2017, 7, 24)) / 86400000))
    }
  }
}
</script>

<style lang="sass" scoped>
.siaaaaam
  margin-top: 15px
  text-align: center

.marquee-container
  float: left
  width: 100vw
  margin: 0 auto
  white-space: nowrap
  overflow: hidden
  box-sizing: border-box

.marquee-container .marquee
  line-height: 80vh
  font-size: 80vh
  display: inline-block
  padding-left: 100%
  animation: marquee 15s linear infinite

@keyframes marquee
  0%
    transform: translate(0, 0)
  100%
    transform: translate(-100%, 0)
</style>
