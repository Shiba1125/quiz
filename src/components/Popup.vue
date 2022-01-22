<template>
  <div class="mask">
      <div class="popup-wrapper">
          <div class="close" @click="$emit('close')">X</div>
          <slot name="title" class="title" :data="title">{{title}}</slot>
          <slot name="content" class="content" :data="content">{{content}}</slot>
          <div class="add-btn" @click="addCount()">+</div>
      </div>
  </div>
</template>

<script>
export default {
    props: ['title', 'content'],
    
    methods: {
        addCount() {
            this.$store.commit('addCount')
        },
    }
}
</script>

<style scoped>
.mask {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: 999;
    background: rgba(0, 0, 0, 0.5);
}

.popup-wrapper {
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 300px;
    height: 300px;
    background: white;
    border-radius: 18px;
}

.title {
    width: 100%;
    height: 80px;
    line-height: 80px;
    text-align: center;
    background: greenyellow;
    border-radius: 18px 18px 0 0 ;
}

.content {
    width: 70%;
    height: 120px;
    line-height: 120px;
    text-align: center;
    margin: 30px auto;
}

.close {
    position: absolute;
    right: 0;
    top: 10px;
    width: 50px;
    height: 50px;
    font-size: 40px;
    font-weight: 600;
}

.add-btn {
    position: absolute;
    font-size: 40px;
    font-weight: 600;
    text-align: center;
    bottom: 10px;
    left: 20px;
}
</style>