<template>
    <form @submit="addPost" class="new-post-form">
        <div class="new-post-form__title">Add New Post!</div>

        <main-input
            v-model="post.title"
            placeholder="New post Title"
            type="text"
        />

        <main-input
            v-model="post.body"
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
            body: "",
        },
    }),

    watch: {
        //(?) В случае когда мы следим за объектом,
        //    нам нужно включить режим "глубокого" отслеживания.
        post: {
            handler(newValue) {
                //...
            },
            deep: true,
        },
    },
    methods: {
        addPost(e) {
            e.preventDefault()

            this.$emit("addNewPost", { ...this.post, id: Date.now() })

            this.post.body = ""
            this.post.title = ""
        },
    },
}
</script>

<style scoped>
.new-post-form {
    color: white;
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.new-post-form__title {
    font-size: 1.4em;
}
</style>
