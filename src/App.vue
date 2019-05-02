<template>
  <div class="root">
    <div class="item" v-for="(text,index) in fizzBuzz" :key="index">{{text}}</div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { Watch, Component } from 'vue-property-decorator'

@Component
export default class extends Vue {
  numbers = [...Array(101).keys()].slice(1)

  keys: { [index: number]: string } = {
    3: 'Fizz',
    5: 'Buzz'
  }

  get fizzBuzz() {
    return this.numbers.map(num => {
      var ret = ''
      Object.keys(this.keys).forEach(key => {
        var keyNum = parseInt(key)
        if (num % keyNum === 0) ret += this.keys[key]
      })
      return ret.length > 0 ? ret : num
    })
  }
}
</script>

<style lang="scss">
body {
  background: rgb(236, 236, 236);
  display: flex;
  flex-direction: column;
  align-items: center;
}

.root {
  font-family: 'Roboto';
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  font-size: 16px;
  max-width: 80rem;
}

.item {
  width: 12rem;
  border: 1px solid gray;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem;
  margin: 0.5rem;
  background: white;
  border-radius: 0.4rem;
}

.item:hover {
  background: rgb(240, 240, 240);
}
</style>