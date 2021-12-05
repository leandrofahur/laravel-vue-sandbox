<template>
    <div class="addItem">
        <input type="text" v-model="item.name" />
        <font-awesome-icon
            icon="plus-square"
            :class="[item.name ? 'active' : 'inactive', 'plus']"
            @click="addItem()"
        />
    </div>
</template>

<script>
export default {
    data: function () {
        return {
            item: {
                name: "",
            },
        };
    },

    methods: {
        addItem() {
            if (this.item.name == "") {
                return;
            }

            axios
                .post("api/item/store", {
                    item: this.item,
                })
                .then((response) => {
                    if (response.status == 201) {
                        this.item.name = "";
                    }
                })
                .catch((err) => console.log(err));
        },
    },
};
</script>

<style scoped>
.addItem {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}

input {
    background: #fff;
    border: 0;
    outline: none;
    padding: 5px;
    margin-right: 5px;
    width: 100%;
}

.plus {
    font-size: 25px;
}

.active {
    color: #00ce25;
}

.inactive {
    color: #999999;
}
</style>
