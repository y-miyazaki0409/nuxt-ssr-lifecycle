<template>
  <div>
    <InLayoutSample />
    <nuxt />
  </div>
</template>

<script>
  import InLayoutSample from '~/components/InLayoutSample.vue'

  export default {
    components: {
      InLayoutSample
    },
    data() {
      return {
        hoge: 'hogehoge'
      }
    },
    asyncData () {
      if (process.server) {
        console.log(`[InLayoutSample] SSR in asyncData | this.hoge error`) // hogeはundefinedエラー
      } else {
        console.log(`[InLayoutSample] CSR in asyncData | this.hoge error`) // hogeはundefinedエラー
      }
    },
    fetch () {
      if (process.server) {
        console.log(`[InLayoutSample] SSR in fetch | `, this.hoge, this.computedHoge)
      } else {
        console.log(`[InLayoutSample] CSR in fetch | `, this.hoge, this.computedHoge)
      }
    },
    validate({ params, query, store }) {
      if (process.server) {
        console.log(`[InLayoutSample] SSR in validate | `, this.hoge, this.computedHoge)
      } else {
        console.log(`[InLayoutSample] CSR in validate | `, this.hoge, this.computedHoge)
      }
      return true
    },
    beforeCreate () {
      if (process.server) {
        console.log(`[InLayoutSample] SSR in beforeCreate | `, this.hoge, this.computedHoge)
      } else {
        console.log(`[InLayoutSample] CSR in beforeCreate | `, this.hoge, this.computedHoge)
      }
    },
    created () {
      if (process.server) {
        console.log(`[InLayoutSample] SSR in created | `, this.hoge, this.computedHoge)
      } else {
        console.log(`[InLayoutSample] CSR in created | `, this.hoge, this.computedHoge)
      }
    },
    beforeMount () {
      if (process.server) {
        console.log(`[InLayoutSample]　SSR in beforeMount | `, this.hoge, this.computedHoge)
      } else {
        console.log(`[InLayoutSample]　CSR in beforeMount | `, this.hoge, this.computedHoge)
      }
    },
    mounted () {
      if (process.server) {
        console.log(`[InLayoutSample]　SSR in mounted | `, this.hoge, this.computedHoge)
      } else {
        console.log(`[InLayoutSample]　CSR in mounted | `, this.hoge, this.computedHoge)
      }
    },
    computed: {
      computedHoge () {
        return `computed_${this.hoge}`
      }
    }
  }
</script>

<style>
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
</style>
