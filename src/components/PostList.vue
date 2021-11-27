<template>
    <div class="container">
        <h2>Posts List:</h2>
        <post-item
            @delete="$emit('delete', post.id)"
            v-for="post in posts"
            :post="post"
            :key="post.id"
        />
    </div>
</template>

<script>
import PostItem from "@/components/PostItem"

export default {
    components: { PostItem },
    props: {
        posts: {
            type: Array,
            required: true,
        },
    },
}
</script>

<style scoped>
.container {
    padding: 10px;
    display: flex;
    flex-direction: column;
    gap: 10px;
}
</style>
