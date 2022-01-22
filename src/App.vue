<template>
  <div id="app">
    <div class="father-wrapper">
      <h1 class="title">我是父層</h1>
      <div class="open-popup" @click="isShow = true">~~點我打開彈窗~~</div>
      <div class="count-wrapper">count: {{count}}</div>
      <input type="text" placeholder="自訂Popup Title!" v-model="title"/>
      <input type="text" placeholder="自訂Popup Content!" v-model="content"/>
    </div>
    <Popup v-if="isShow" @close="close" :title="title" :content="content">
      <div slot="title" class="title" slot-scope="title">{{title.data}}</div>
      <div slot="content" class="content" slot-scope="content">{{content.data}}</div>
    </Popup>
  </div>
</template>

<script>
import Popup from './components/Popup.vue'

export default {
  name: 'App',

  data() {
    return {
      isShow: false,
      title: 4567,
      content:4567,
    }
  },

  async mounted() {
    const arr = [1, 2, 3, 4, 5]
    let time;

    for(let i = 0; i < arr.length; i++) {
      time = Math.round(Math.random() * 5)
      await print(i)
    }

    function print(i) {
        return new Promise((res) => {
        setTimeout(() => {
          console.log(arr[i])
          res()
        }, time * 1000)
      })
      }
  },

  components: {
    Popup,
  },

  methods: {
    close() {
      this.isShow = false
    }
  },

  computed: {
    count() {
      return this.$store.state.count
    },
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

.open-popup {
  height: 30px;
  line-height: 30px;
  width: 150px;
  text-align: center;
  border-radius: 100px;
  box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.4);
  background: palevioletred;
  cursor: pointer;
}
</style>
