<template>
    <div class="app">
        <new-post-form @addNewPost="handleNewPost" />
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
            this.posts = [...this.posts, post]
            // this.posts.push(post)
        },
        deletePost(postId) {
            console.log("post id", postId)

            this.posts = this.posts.filter(({ id }) => id !== postId)
        },
    },
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body {
    background: #303030;
    color: yellowgreen;
    overflow: overlay;
}
</style>
