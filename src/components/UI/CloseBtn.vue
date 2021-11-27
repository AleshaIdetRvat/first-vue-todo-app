<template>
    <button class="close-btn" aria-label="delete"><i>+</i></button>
</template>

<script>
export default {}
</script>

<style scoped>
.close-btn {
    transition: 0.2s;
    cursor: pointer;
    width: 30px;
    height: 30px;
    background: tomato;
    border: none;
    border-radius: 6px;
}
.close-btn:hover {
    opacity: 0.6;
}

.close-btn > i {
    display: flex;
    flex-direction: column;
    align-items: center;

    transform: rotate(45deg) translate(-1px, -3px);
    width: 100%;
    height: 100%;
    font-size: 2.5em;
    line-height: 110%;
}
</style>
