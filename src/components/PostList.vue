<template>
    <!--(-) Вариант с v-show - element не удаляется, добавляется display: none <div v-show="posts.length > 0" class="column"> -->
    <div v-show="posts.length > 0" class="column">
        <h2>Posts List:</h2>

        <transition-group class="list" name="list-complete" tag="div">
            <post-item
                class="list-complete-item"
                @delete="$emit('delete', post.id)"
                v-for="post in posts"
                :post="post"
                :key="post.id"
            />
        </transition-group>
    </div>

    <h2 v-show="!(posts.length > 0)" class="empty-title">Posts not found 🍃</h2>
</template>

<script>
import PostItem from "@/components/PostItem"

export default {
    components: { PostItem },
    emits: ["delete"],
    data() {
        return {
            items: [1, 3, 5, 6, 7, 8, 9],
        }
    },
    props: {
        posts: {
            type: Array,
            required: true,
        },
    },
}
</script>

<style>
.list-move {
}
.list-complete-item {
    transition: 0.4s;
}

.list-complete-enter-from,
.list-complete-leave-to {
    opacity: 0;
    transform: scale(80%);
    /* height: 50%; */
}

.list-complete-leave-active {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
}

.column,
.list {
    width: 100%;

    transition: 1s;
    display: flex;
    flex-direction: column;
    gap: 10px;
}
.list {
    flex: 1 1 auto;
    position: relative;
}

.empty-title {
    text-align: center;
    padding: 10px;
}
</style>
