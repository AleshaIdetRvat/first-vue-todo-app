<template>
    <div class="container">
        <article class="post" v-for="post in posts" :key="post.id">
            <h2 class="post__title">
                <strong>Название:</strong> {{ post.title }}
            </h2>
            <section class="post__content">
                <h3 class="post__second-title">Описание:</h3>
                <p class="post__description">
                    {{ post.content }}
                </p>
            </section>
        </article>
    </div>
</template>

<script>
export default {
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

.post {
    padding: 15px;
    background: rgb(51, 51, 51);
    box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.3);
    border-radius: 12px;
}

.post__title {
}

.post__content {
    color: whitesmoke;
    opacity: 0.8;
}

.post__second-title {
    font-size: 1em;
}

.post__description {
    font-size: 0.8em;
}
</style>
