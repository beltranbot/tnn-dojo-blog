<template>
  <div class="home">
    <h1>Home</h1>
    <input type="text" v-model="search">
    <p>search term - {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">
      {{ name }}
    </div>
    <button @click="handleClick">stop watching</button>
  </div>
</template>

<script>
import { reactive, ref } from '@vue/reactivity'
import { computed, watch, watchEffect } from '@vue/runtime-core'

export default {
  name: 'Home',
  setup() {
    const search = ref('')
    const names = ref([
      'mario',
      'yoshi',
      'luigi',
      'toad',
      'bowser',
      'koopa',
      'peach'
    ])
    const stopWatch = watch(search, () => {
      console.log("watch function ran")
    })
    // watchEffect watches for any change on the dependencies of the function
    const stopEffect = watchEffect(() => {
      console.log("watchEffect function ran", search.value)
    })
    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value))
    })
    const handleClick = () => {
      stopWatch()
      stopEffect()
    }
    return {
      names,
      search,
      matchingNames,
      handleClick
    }
  }
}
</script>
