<template>
  <div :style="myStyle">
  </div>
</template>

<script>
import { picasso } from '@vechain/picasso'

export default {
  props: {
    address: String, // eg. 0xabcdefg
    myHeight: String, // eg. 100px
    myWidth: String // eg. 100px
  },
  methods: {
    createBackground (address) {
      const mySVG = picasso(address)
      return `no-repeat url('data:image/svg+xml,${mySVG}')`
    }
  },
  computed: {
    myStyle () {
      const bg = this.createBackground(this.address)
      return {
        // 'filter':'saturate(200%)',
        'border-radius': this.myHeight,
        height: this.myHeight,
        width: this.myWidth,
        background: bg
      }
    }
  }
}
</script>
