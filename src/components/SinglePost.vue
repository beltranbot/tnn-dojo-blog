<template>
    <div class="post">
        <router-link :to="{ name: 'Details', params: {id: post.id}}">
            <h3>{{ post.title }}</h3>
        </router-link>
        <p>{{ snippet }}</p>
        <Tags :tags="post.tags" />
    </div>
</template>

<script>
import { computed } from '@vue/runtime-core'
import Tags from './Tags'
export default {
    props: ["post"],
    setup(props) {
        const snippet = computed(() => props.post.body.substr(0, 100) + "...")
        return { snippet }
    },
    components: { Tags }
}
</script>

<style>

</style>