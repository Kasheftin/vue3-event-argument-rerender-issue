<template>
  <div>
    <button @click="randomize">
      Randomize
    </button>
    <Dummy 
      v-for="id in ids"
      :key="id"
      :id="id"
      @dummy-event="dummyEventHandler(id)"
    />
  </div>
</template>

<script>
import Dummy from './components/Dummy.vue'

export default {
  name: 'App',
  components: {
    Dummy
  },
  data () {
    return {
      ids: [1, 2, 3, 4, 5]
    }
  },
  methods: {
    dummyEventHandler (...args) {
      console.log('dummy event', args)
    },
    randomize () {
      const ids = [...this.ids]
      const newIds = []
      while (ids.length) {
        const r = Math.floor(Math.random() * ids.length)
        newIds.push(ids[r])
        ids.splice(r, 1)
      }
      this.ids = newIds
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
