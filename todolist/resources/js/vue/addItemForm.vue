<template>
    <div class="addItem">
        <input type="text" v-model="item.name" />
        <font-awesome-icon
            icon="plus-square"
            :class="[item.name ? 'active' : 'disabled', 'plus']"
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
};
</script>

<style scoped>
.addItem {
    display: flex;
    justify-content: center;
    align-items: center;
}

input {
    background: #f7f7f7;
    outline: none;
    border: 0px;
    padding: 5px;
    margin-right: 10px;
    width: 100%;
}

.plus {
    font-size: 20px;
}

.active {
    color: #00ce25;
}

.disabled {
    color: #999999;
}
</style>
