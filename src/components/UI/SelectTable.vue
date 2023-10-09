<template>
    <select class="select" :value="modelValue">
        <option disabled value="">Выберите действие</option>
        <option
            v-for="option in options"
            :key="option.value"
            :value="options.value"
        >
            {{ option.name }}
        </option>
    </select>
</template>
<script>
export default {
    name: "select-table",
    props: {
        modelValue: {
            type: String,
        },
        options: {
            type: Array,
            default: () => [],
        },
    },
};
</script>
<style scoped lang="scss">
.select {
    cursor: pointer;
}
</style>
