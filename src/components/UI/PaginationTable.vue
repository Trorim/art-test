<template>
    <div class="pagination">
        <div
            v-for="pageNumber in numberOfPages"
            :key="pageNumber"
            class="pagination-item"
            @click="$emit('update', pageNumber)"
            :class="{ active: page === pageNumber }"
        >
            {{ pageNumber }}
        </div>
    </div>
</template>

<script>
export default {
    name: "pagination-table",
    props: {
        numberOfPages: {
            type: Number,
        },
        page: {
            type: Number,
        },
    },
};
</script>

<style scoped lang="scss">
.pagination {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
    margin-top: 30px;
    &-item {
        border: 1px solid grey;
        padding: 10px;
        transition: all 0.3s ease;
        &:hover {
            cursor: pointer;
            background-color: grey;
            color: #fff;
        }
    }
    .active {
        background-color: grey;
        color: #fff;
    }
}
</style>
