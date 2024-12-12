<template>
    <div>
        <Post :post="post[i]" v-for="(Post, i) in post" :key="i" />
    </div>
</template>
<script>
import Post from './Post.vue';
export default {
    name: 'Container',
    data() {
        return {};
    },
    components: {
        Post: Post
    },
    props: {
        post: Array
    }
};
</script>
<style>
div {
    background: beige;
}
</style>
