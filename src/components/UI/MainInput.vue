<template>
    <input :value="modelValue" @input="changeHandler" class="main-input" />
</template>

<script>
export default {
    name: "main-input",

    props: {
        modelValue: [String, Number],
    },

    methods: {
        changeHandler(event) {
            this.$emit("update:modelValue", event.target.value)
        },
    },
}
</script>

<style scoped>
.main-input {
    padding: 8px;
    border: none;
    background: var(--white);
    box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.1);
    border-radius: 6px;
}
</style>
