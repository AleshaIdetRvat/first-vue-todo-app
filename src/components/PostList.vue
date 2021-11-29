<template>
    <!--(-) Вариант с v-show - не удаляется, добавляется display: none <div v-show="posts.length > 0" class="container"> -->
    <div v-if="posts.length > 0" class="container">
        <h2>Posts List:</h2>
        <post-item
            @delete="$emit('delete', post.id)"
            v-for="post in posts"
            :post="post"
            :key="post.id"
        />
    </div>

    <h2 v-else class="empty-title">Posts not found 🍃</h2>
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

.empty-title {
    text-align: center;
    padding: 10px;
}
</style>
