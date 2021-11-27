// @submit="addNewPost"

<template>
    <form @submit="addPost" class="new-post-form">
        <div class="new-post-form__title">Add New Post!</div>

        <input
            v-model="post.title"
            class="new-post-form__input"
            type="text"
            placeholder="New post Title"
        />

        <input
            v-model="post.content"
            class="new-post-form__input"
            type="text"
            placeholder="New post text"
        />

        <main-btn type="submit"> Create </main-btn>
    </form>
</template>
<script>
import MainBtn from "@/components/UI/MainBtn"

export default {
    components: {
        MainBtn,
    },
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
    background-color: rgb(77, 77, 77);
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.new-post-form__title {
}

.new-post-form__input {
    padding: 8px;
    border: none;
    background: rgb(207, 207, 207);
    box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.1);
    border-radius: 6px;
}
</style>
