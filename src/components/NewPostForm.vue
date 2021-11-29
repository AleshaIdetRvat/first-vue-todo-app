// @submit="addNewPost"

<template>
    <form @submit="addPost" class="new-post-form">
        <div class="new-post-form__title">Add New Post!</div>

        <main-input
            v-model="post.title"
            placeholder="New post Title"
            type="text"
        />

        <main-input
            v-model="post.content"
            placeholder="New post text"
            type="text"
        />

        <main-btn type="submit"> Create </main-btn>
    </form>
</template>
<script>
export default {
    data: () => ({
        post: {
            title: "",
            content: "",
        },
    }),
    methods: {
        addPost(e) {
            e.preventDefault()
            this.post.id = Date.now()

            this.$emit("addNewPost", { ...this.post })

            // После добавления поста очищаем инпуты
            this.post.content = ""
            this.post.title = ""
        },
    },
}
</script>

<style scoped>
.new-post-form {
    padding: 15px;
    color: white;
    /* background-color: rgb(77, 77, 77); */
    /* border-radius: 8px; */
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.new-post-form__title {
    font-size: 1.4em;
}
</style>
