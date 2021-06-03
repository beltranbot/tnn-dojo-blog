<template>
    <span v-for="tag in tags" :key="tag">
        #{{tag}}
    </span>
</template>

<script>
export default {
    props: ["tags"]
}
</script>

<style>

</style>