<template>
  <div class="home">
    <h1>Home</h1>
    <h2>Refs</h2>
    <p>{{ ninjaOne.name }} - {{ ninjaOne.age }}</p>
    <button @click="updateNinjaOne">update ninja one</button>
    <h2>Reactive</h2>
    <p>{{ ninjaTwo.name }} - {{ ninjaTwo.age }}</p>
    <button @click="updateNinjaTwo">update ninja two</button>
  </div>
</template>

<script>
import { reactive, ref } from '@vue/reactivity'

export default {
  name: 'Home',
  setup() {
    const ninjaOne = ref({
      name: "mario",
      age: 30
    })
    // you can't use primitive values with reactive
    const ninjaTwo = reactive({
      name: "luigi",
      age: 35
    })
    const updateNinjaOne = () => {
      ninjaOne.value.age = 40
    }

    const updateNinjaTwo = () => {
      ninjaTwo.age = 45
    }

    return { ninjaOne, ninjaTwo, updateNinjaOne, updateNinjaTwo }
  }
}
</script>
