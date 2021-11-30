<template>
    <select :value="modelValue" @change="changeHandler">
        <option disabled selected value="">Выберите из списка</option>

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

<style scoped></style>
