<template>
    <input :value="modelValue" @input="updateInput" class="main-input" />
</template>

<script>
export default {
    name: "main-input",

    props: {
        modelValue: [String, Number],
    },

    methods: {
        updateInput(e) {
            this.$emit("update:modelValue", e.target.value)
        },
    },
}
</script>

<style scoped>
.main-input {
    padding: 8px;
    border: none;
    background: rgb(207, 207, 207);
    box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.1);
    border-radius: 6px;
}
</style>
