<template>
  <div>
    <input type="text" v-model="myValue">
    <!-- {{ myValueWithoutNum }} -->
    {{ getMyValWihoutNum() }}
    <ul>
      <li v-for="item in myList">{{item.name}} + {{item.price}}</li>
    </ul>
    <button @click="changeList">change</button>
  </div>
</template>

<script>
import Vue from 'vue'
export default {
  data () {
    return {
      myValue: '',
      myList: [
        {
          name: 'apple',
          price: 34
        },
        {
          name: 'banana',
          price: 36
        }
      ]
    }
  },
  computed: {
    myValueWithoutNum: function () {
      // return this.myValue.replace(/\d/g, '')
      return Date.now()
    }
  },
  methods: {
    getMyValWihoutNum () {
      return this.myValue.replace(/\d/g, '')
    },
    changeList () {
      Vue.set(this.myList, 1, {
        name: 'pinapple',
        price: 78
      })
      // this.tellUser()
    },
    removeItem () {
      // this.tellUser()
    },
    tellUser () {
      alert('list change')
    }
  },
  watch: {
    myValue: function (val, oldVal) {
      console.log(val, oldVal)
    },
    myList: function () {
      this.tellUser()
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
