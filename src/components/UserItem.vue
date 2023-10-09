<template>
    <div class="user">
        <div class="user__item">{{ user.id }}</div>
        <div class="user__item">
            {{
                user.name.length >= 27
                    ? user.name.slice(0, 24) + "..."
                    : user.name
            }}
        </div>
        <div class="user__item">{{ user.age }}</div>
        <div class="user__item">{{ lastLoginUser }}</div>
        <div class="user__item">
            <select-table :options="options" />
        </div>
    </div>
</template>

<script>
import SelectTable from "@/components/UI/SelectTable";

export default {
    components: {
        SelectTable,
    },
    name: "user-item",
    props: {
        user: {
            type: Object,
        },
    },
    data() {
        return {
            date: new Date(this.user.lastLogin),
            options: [
                { type: "delete", name: "Удалить" },
                { type: "change", name: "Изменить" },
                { type: "favorite", name: "Добавить в избранное" },
            ],
        };
    },
    methods: {
        login(time) {
            return this.date[time]() < 10
                ? "0" + this.date[time]()
                : this.date[time]();
        },
    },
    computed: {
        lastLoginUser() {
            return `
                ${this.login("getDate")}.
                ${this.login("getMonth")}.
                ${this.date.getFullYear()} 
                ${this.login("getHours")}:${this.login(
                "getMinutes"
            )}:${this.login("getSeconds")} 
            `;
        },
    },
};
</script>

<style lang="scss">
.user {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    align-content: center;
    padding: 15px 0;
    margin-top: 10px;

    &__item {
        justify-self: center;
        overflow: hidden;
    }
}
</style>
