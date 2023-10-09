<template>
    <div class="table">
        <div class="table-header">
            <div @click="$emit('update', 'id')" class="table-header__item sort">
                ID &#8634;
            </div>
            <div class="table-header__item">Name</div>
            <div
                @click="$emit('update', 'age')"
                class="table-header__item sort"
            >
                Age &#8634;
            </div>
            <div class="table-header__item">Last login</div>
            <div class="table-header__item">Action</div>
        </div>
        <div v-if="pagination.length > 0">
            <user-item v-for="user in pagination" :key="user.id" :user="user" />
        </div>
        <div v-else class="empty">
            По этому запросу пользователь не найден: {{ searchValue }}
        </div>
    </div>
</template>

<script>
import UserItem from "@/components/UserItem";

export default {
    components: {
        UserItem,
    },
    name: "user-table",
    props: {
        pagination: {
            type: Array,
        },
        searchValue: {
            type: String,
        },
    },
};
</script>

<style scoped lang="scss">
.table {
    margin-top: 30px;
    .table-header {
        display: grid;
        grid-template-columns: repeat(5, 1fr);
        border-bottom: 2px solid grey;
        align-content: center;
        padding: 15px 0;
        &__item {
            justify-self: center;
        }
        .sort {
            cursor: pointer;
        }
    }
    .empty {
        text-align: center;
        font-size: 30px;
        margin-top: 30px;
        color: red;
    }
}
</style>
