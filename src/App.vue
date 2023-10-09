<template>
    <div class="container">
        <input-table v-model="searchValue" />
        <user-table
            :pagination="pagination"
            :searchValue="this.searchValue"
            @update="sortedPosts"
        />
        <pagination-table
            @update="changePage"
            :numberOfPages="numberOfPages"
            :page="this.page"
        />
    </div>
</template>
<script>
import UserTable from "./components/UserTable";
import InputTable from "@/components/UI/InputTable";
import PaginationTable from "@/components/UI/PaginationTable";

export default {
    data() {
        return {
            users: [
                {
                    id: 1,
                    name: "John Sina",
                    age: 25,
                    lastLogin: Date.now(),
                },
                {
                    id: 2,
                    name: "Stan Smith",
                    age: 32,
                    lastLogin: Date.now() - 56810,
                },
                {
                    id: 3,
                    name: "Edgar Po",
                    age: 80,
                    lastLogin: Date.now() - 3255320,
                },
                {
                    id: 4,
                    name: "Leanne Graham",
                    age: 23,
                    lastLogin: Date.now() - 23530,
                },
                {
                    id: 5,
                    name: "Ervin Howell",
                    age: 33,
                    lastLogin: Date.now() - 54352340,
                },
                {
                    id: 6,
                    name: "Clementine Bauch",
                    age: 35,
                    lastLogin: Date.now() - 64650,
                },
                {
                    id: 7,
                    name: "Patricia Lebsack",
                    age: 20,
                    lastLogin: Date.now() - 2222260,
                },
                {
                    id: 8,
                    name: "Chelsey Dietrich",
                    age: 44,
                    lastLogin: Date.now() - 4470,
                },
                {
                    id: 9,
                    name: "Dennis Schulist",
                    age: 37,
                    lastLogin: Date.now() - 23480,
                },
                {
                    id: 10,
                    name: "Kurtis Weissnat",
                    age: 71,
                    lastLogin: Date.now() - 23490,
                },
                {
                    id: 11,
                    name: "Nicholas Runolfsdottir",
                    age: 59,
                    lastLogin: Date.now() - 454100,
                },
                {
                    id: 12,
                    name: "Glenna Reichert",
                    age: 50,
                    lastLogin: Date.now() - 454150,
                },
                {
                    id: 13,
                    name: "Clementina DuBuque",
                    age: 60,
                    lastLogin: Date.now() - 546546250,
                },
                {
                    id: 14,
                    name: "Luis Clement",
                    age: 18,
                    lastLogin: Date.now() - 234234350,
                },
                {
                    id: 15,
                    name: "Povar Rovar",
                    age: 37,
                    lastLogin: Date.now() - 4450,
                },
                {
                    id: 16,
                    name: "Plever Clever",
                    age: 67,
                    lastLogin: Date.now() - 445550,
                },
                {
                    id: 17,
                    name: "Romaguera Crona",
                    age: 58,
                    lastLogin: Date.now() - 56456650,
                },
                {
                    id: 18,
                    name: "Deckow Crist",
                    age: 79,
                    lastLogin: Date.now() - 568568750,
                },
                {
                    id: 19,
                    name: "Romaguera Jacobson",
                    age: 83,
                    lastLogin: Date.now() - 658568850,
                },
                {
                    id: 20,
                    name: "Robel Corkery",
                    age: 90,
                    lastLogin: Date.now() - 13413413950,
                },
                {
                    id: 21,
                    name: "Keebler LLC",
                    age: 49,
                    lastLogin: Date.now() - 1341431050,
                },
                {
                    id: 22,
                    name: "Considine Lockman",
                    age: 34,
                    lastLogin: Date.now() - 1363151550,
                },
                {
                    id: 23,
                    name: "Johns Group",
                    age: 29,
                    lastLogin: Date.now() - 1361361362550,
                },
                {
                    id: 24,
                    name: "Abernathy Group",
                    age: 19,
                    lastLogin: Date.now() - 132633550,
                },
                {
                    id: 25,
                    name: "Edgar Po",
                    age: 30,
                    lastLogin: Date.now() - 1005050,
                },
            ],
            searchValue: "",
            page: 1,
            usersOnPage: 5,
        };
    },
    components: {
        UserTable,
        InputTable,
        PaginationTable,
    },
    methods: {
        sortedPosts(prop) {
            return this.usersArr.sort((a, b) => a[prop] - b[prop]);
        },
        changePage(pageNumber) {
            this.page = pageNumber;
        },
    },
    computed: {
        usersArr() {
            return this.users;
        },
        searchUserName() {
            this.changePage(1);
            return this.users.filter((user) =>
                user.name.toLowerCase().includes(this.searchValue.toLowerCase())
            );
        },
        numberOfPages() {
            return Math.ceil(this.searchUserName.length / this.usersOnPage);
        },
        pagination() {
            let from = (this.page - 1) * this.usersOnPage,
                to = from + this.usersOnPage;
            return this.searchUserName.slice(from, to);
        },
    },
};
</script>

<style lang="scss">
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}
body {
    font-family: "Lato", sans-serif;
}
.container {
    max-width: 1000px;
    margin: 50px auto;
}
</style>
