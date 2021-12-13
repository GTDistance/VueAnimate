<template>
  <div class="container">
    <button @click="switchBtn">切换</button>
    <transition name="fade">
      <p v-if="isNum" class="ani-p">我是一只小小鸟</p>
    </transition>

    <button @click="show = !show">Toggle show</button>
    <transition name="bounce">
      <p v-if="show">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris
        facilisis enim libero, at lacinia diam fermentum id. Pellentesque
        habitant morbi tristique senectus et netus.
      </p>
    </transition>
    <component :is="view"></component>

  </div>

  <!-- <input v-model="view" type="radio" value="a" id="a" /><label for="a"
    >A</label
  >
  <input v-model="view" type="radio" value="b" id="b" /><label for="b"
    >B</label
  > -->
  <!-- <transition name="component-fade" mode="out-in">
    <component :is="view"></component>
  </transition> -->
</template>
<script>
export default {
  components: {
    "a": {
      template: "<div>Component A</div>"
    },
    "b": {
      template: "<div>Component B</div>"
    }
  },
  data() {
    return {
      isNum: true,
      flag1: true,
      flag2: true,
      flag: true,
      show: true,
      view: 'a',
    }
  },
  //生命周期 - 创建完成（访问当前this实例）
  created() {},
  //生命周期 - 挂载完成（访问DOM元素）
  mounted() {},
  methods: {
    switchBtn() {
      this.isNum = !this.isNum
    },
  },
}
</script>
<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.ani-p {
  background: yellow;
  /* display: inline-block; */
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateX(80px) translateY(80px);
}
.fade-enter-active,
.fade-leave-active {
  transition: all 1s ease;
}

.bounce-enter-active {
  animation: bounce-in 0.5s;
}
.bounce-leave-active {
  animation: bounce-in 0.5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(1);
  }
}

.component-fade-enter-active,
.component-fade-leave-active {
  transition: opacity 0.3s ease;
}

.component-fade-enter-from,
.component-fade-leave-to {
  opacity: 0;
}
.demo {
  font-family: sans-serif;
  border: 1px solid #eee;
  border-radius: 2px;
  padding: 20px 30px;
  margin-top: 1em;
  margin-bottom: 40px;
  user-select: none;
  overflow-x: auto;
}
</style>
