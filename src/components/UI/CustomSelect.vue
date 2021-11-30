<template>
    <select class="select" :value="modelValue" @change="changeHandler">
        <option class="select__option" disabled selected value="">
            Выберите из списка
        </option>

        <option v-for="item in options" :key="item.value" :value="item.value">
            {{ item.name }}
        </option>
    </select>
</template>

<script>
export default {
    name: "custom-select",
    props: {
        modelValue: {
            type: String,
        },
        options: {
            type: Array,
            default: () => [],
        },
    },
    methods: {
        changeHandler(event) {
            this.$emit("update:modelValue", event.target.value)
        },
    },
}
</script>

<style scoped>
.select {
    cursor: pointer;
    padding: 8px;
    border-radius: 8px;
    background: var(--white);
}
.select__option {
}
</style>
