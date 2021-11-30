<template>
    <div @click="handleClick" class="pagination">
        <span
            v-for="page in totalPagesCount"
            class="pagination__item"
            :class="{
                '--current': currentPage === page,
            }"
            :key="page"
            >{{ page }}</span
        >
    </div>
</template>

<script>
export default {
    methods: {
        handleClick(event) {
            if (event.target.className === "pagination__item") {
                this.$emit("update:currentPage", +event.target.innerText)
            }
        },
    },
    props: {
        totalPagesCount: { type: Number, default: 0 },
        currentPage: { type: Number, default: 1 },
    },
}
</script>

<style scoped>
.pagination {
    margin-top: 20px;
    width: 100%;
    display: flex;
    justify-content: center;
}
.pagination__item {
    user-select: none;
    cursor: pointer;
    transition: 0.2s;
    padding: 5px 10px;
    border-radius: 4px;
    background-color: rgba(255, 255, 255, 0);
    color: var(--green);
    border-bottom: 3px solid transparent;
}

.pagination__item:hover {
    background-color: rgba(255, 255, 255, 0.1);
    box-shadow: 0px 1px 4px rgba(255, 255, 255, 0.05);
}
.pagination__item.--current {
    border-bottom: 3px solid var(--green);
}
</style>
