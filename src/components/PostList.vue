<template>
    <div class="post-list">
        <div v-for="post in posts" :key="post.id">
            <SinglePost :post="post"/>
        </div>
    </div>
</template>

<script>
import SinglePost from "./SinglePost"
export default {
    name: "PostList",
    props: ["posts"],
    setup(props) {

    },
    components: { SinglePost }
}
</script>

<style>

</style>