<template>
    <div v-if="isShow" class="modal" @click="hideModal">
        <div @click.stop class="modal__container">
            <div class="modal__column">
                <close-btn @click="hideModal" style="align-self: flex-end" />
                <slot></slot>
            </div>
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
@keyframes showing-animation {
    0% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
}
@keyframes showing-translate-animation {
    0% {
        transform: scale(80%);
    }

    100% {
        transform: scale(100%);
    }
}
.modal {
    animation: showing-animation 0.3s ease forwards;

    opacity: 0;
    position: fixed;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    display: flex;
    align-items: center;
    justify-content: center;

    background-color: #000000b0;
}

.modal__container {
    animation: showing-translate-animation 0.3s ease forwards;

    min-width: 33vw;
    padding: 20px;
    border-radius: 8px;

    background-color: var(--black);
}

.modal__column {
    display: flex;
    flex-direction: column;
    gap: 15px;
}
</style>
