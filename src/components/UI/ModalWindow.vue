<template>
    <div v-if="isShow" class="modal">
        <div @click.stop class="modal__container">
            <slot></slot>
        </div>
    </div>
</template>

<script>
export default {
    name: "modal-window",
    props: {
        isShow: {
            type: Boolean,
            default: false,
        },
    },
    methods: {
        hideModal() {
            this.$emit("update:isShow", false)
        },
    },
}
</script>

<style scoped>
.modal {
    position: fixed;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    display: flex;
    align-items: center;
    justify-content: center;

    background-color: #00000090;
}

.modal__container {
    padding: 15px;
    border-radius: 8px;

    background-color: var(--black);
}
</style>
