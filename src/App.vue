// note: Остановился на 1ч 7мин ->
https://www.youtube.com/watch?v=XzLuMtDelGk&t=2753s

<template>
    <div class="app">
        <modal-window :isShow="false">
            <new-post-form @addNewPost="handleNewPost" />
        </modal-window>

        <post-list :posts="posts" @delete="deletePost" />
    </div>
</template>

<script>
import NewPostForm from "./components/NewPostForm.vue"
import PostList from "./components/PostList.vue"

export default {
    components: {
        NewPostForm,
        PostList,
    },
    data() {
        return {
            posts: [
                {
                    id: 1,
                    title: "React",
                    content: "asdjfsdfas dff asdf asldkfj asldfl asdfas",
                },
                {
                    id: 2,
                    title: "Vue",
                    content: "asdjf asldkfj asldfl asasd fadfsd    fas",
                },
                {
                    id: 3,
                    title: "Angular",
                    content: "asdjf asldkfj asldfl sfasdfasasdfasdf",
                },
            ],
        }
    },
    methods: {
        handleNewPost(post) {
            this.posts = [post, ...this.posts]
        },
        deletePost(postId) {
            this.posts = this.posts.filter(({ id }) => id !== postId)
        },
    },
}
</script>

<style>
:root {
    --green: yellowgreen;
    --black: #303030;
}
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body {
    background: var(--black);
    color: var(--green);
    overflow: overlay;
}
</style>
