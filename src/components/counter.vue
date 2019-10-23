<template>
  <div id="app">
    <h1>{{ count }}</h1>
    <button @click="decrement()" varient="danger">Decrement</button>
    <button @click="reset()" varient="reset">Reset</button>
    <button @click="increment()" varient="success">Increment</button>
  </div>
</template>

<script>
export default {
  data() {
    return { count: 0 }
  },
  methods: {
    increment() {
      this.count += 1
    },
    decrement() {
      this.count -= 1
    },
    reset() {
      this.count = 0
    }
  },
  mounted() {
    if (localStorage.getItem('count'))
      this.count = JSON.parse(localStorage.getItem('count'))
  },
  watch: {
    count: {
      handler() {
        localStorage.setItem('count', JSON.stringify(this.count))
      },
      deep: true
    }
  }
}
</script>

<style scoped>
span {
  font-weight: bold;
  font-size: 40px / 2;
}
div {
  text-align: center;
  padding: 1em;
  background-color: #fafafa;
  border: 1px solid #ccc;
  border-radius: 3px;
}
</style>
