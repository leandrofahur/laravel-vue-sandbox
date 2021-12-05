<template>
    <div class="container">
        <div class="heading">
            <h2 id="title">Todo List</h2>
            <add-item-form :items="items" />
        </div>
        <list-view />
    </div>
</template>

<script>
import addItemForm from "./addItemForm";
import listView from "./listView";
export default {
    components: {
        addItemForm,
        listView,
    },

    data: function () {
        return {
            items: [],
        };
    },
    methods: {
        getList() {
            axios
                .get("api/items")
                .then((response) => {
                    this.items = response.data;
                })
                .catch((err) => {
                    console.log(err);
                });
        },
    },
    created() {
        this.getList();
    },
};
</script>

<style scoped>
.container {
    width: 350px;
    margin: auto;
}

.heading {
    background: #e6e6e6;
    padding: 10px;
}

#title {
    text-align: center;
}
</style>
