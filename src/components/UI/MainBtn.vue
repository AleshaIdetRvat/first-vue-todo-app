<template>
    <button class="main-btn">
        <slot></slot>
    </button>
</template>

<script>
export default {}
</script>

<style scoped>
.main-btn {
    transition: 0.2s;
    padding: 8px;
    border: none;
    box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.1);
    border-radius: 6px;
    background-color: yellowgreen;
}

.main-btn:hover {
    opacity: 0.7;
}
</style>
