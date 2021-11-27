<template>
    <article class="post">
        <h2 class="post__title"><strong>Название:</strong> {{ post.title }}</h2>

        <close-btn @click="$emit('delete', post.id)" />

        <section class="post__content">
            <h3 class="post__second-title">Описание:</h3>
            <p class="post__description">
                {{ post.content }}
            </p>
        </section>
    </article>
</template>

<script>
export default {
    props: {
        post: {
            type: Object,
            required: true,
        },
    },
}
</script>
<style scoped>
.post {
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 8px;
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
