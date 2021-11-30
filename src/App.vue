<template>
    <div class="app">
        <div class="app__header">
            <main-btn style="margin: 0 auto; display: block" @click="openModal"
                >Создать новый пост 📝
            </main-btn>
            <custom-select v-model="sortOption"></custom-select>
        </div>
        <modal-window v-model:isShow="isModalShow">
            <new-post-form @addNewPost="handleNewPost" />
        </modal-window>

        <post-list v-if="!isLoading" :posts="posts" @delete="deletePost" />
        <h3 v-else>Loading...</h3>
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
            posts: [],
            isModalShow: false,
            testInputValue: "",
            isLoading: true,
            sortOption: "",
        }
    },
    methods: {
        openModal() {
            this.isModalShow = true
        },
        handleNewPost(post) {
            this.posts = [post, ...this.posts]
            this.isModalShow = false
        },
        deletePost(postId) {
            this.posts = this.posts.filter(({ id }) => id !== postId)
        },
        async fetchPosts() {
            try {
                this.isLoading = true

                const data = await fetch(
                    "https://jsonplaceholder.typicode.com/posts?_limit=10"
                )
                const parsedPosts = await data.json()
                this.posts = parsedPosts.map(({ id, title, body }) => ({
                    id,
                    title,
                    content: body,
                }))
            } catch (error) {
                alert(error)
            } finally {
                this.isLoading = false
            }
        },
    },
    mounted() {
        this.fetchPosts()
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
.app {
    padding: 20px 10px;
}
.app__header {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
}
</style>
