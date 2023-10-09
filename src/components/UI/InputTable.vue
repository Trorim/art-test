<template>
    <input
        v-model.trim="inputText"
        type="text"
        class="input"
        placeholder="Имя пользователя"
    />
</template>

<script>
export default {
    name: "input-table",
    data() {
        return {
            inputText: "",
        };
    },
};
</script>

<style scoped lang="scss">
.input {
    width: 300px;
    height: 40px;
    border-radius: 1px solid grey;
    padding: 0 20px;
}
</style>
