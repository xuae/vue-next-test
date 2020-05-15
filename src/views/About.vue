<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h1>test count: {{count}}</h1>
    <div>count * 2 = {{doubleCount}}</div>
    <button @click="add">add</button>
    <div>state from vuex {{a}}</div>
  </div>
</template>
<script>
import { ref, computed, watch, getCurrentInstance  } from 'vue'

export default {
  name: 'About',
  setup() {
    const { ctx } = getCurrentInstance()
    console.log(ctx.$router.currentRoute.value)
    console.log(ctx)

    const count = ref(0)
    const add = () => {
      count.value++
    }
    watch(() => count.value, val => {
      console.log(`count is ${val}`)
    })
    const doubleCount = computed(() => count.value * 2)
    const a = computed(() => ctx.$store.state.test.a)
    return {
      count,
      doubleCount,
      add,
      a
    }
  }
}
</script>
