<template>
    <div class="banner">
        <div class="banner__select">
            <input
                class="banner__checkbox"
                type="checkbox"
                id="selected"
                name="selected"
            >
            <label class="banner__label" for="selected">Selected 2</label>
        </div>
        <button class="banner__button" @click="showPopup = true">Download Selected</button>
    </div>
    <table class="table">
        <thead>
            <tr class="table__row">
                <th class="table__header"></th>
                <th class="table__header">Name</th>
                <th class="table__header">Device</th>
                <th class="table__header">Path</th>
                <th class="table__header">Status</th>
            </tr>
        </thead>
        <tbody>
            <Item
                v-for="item in this.itemsDataList"
                :key="item.name"
                :item="item"
            />
        </tbody>
    </table>
    <div v-if="showPopup" class="popup__overlay">
        <div class="popup__inner">
            <button class="popup__close" @click="showPopup = false">
                <span class="sr-only">Close</span>
            </button>
            <ul>
                <li>Selected 1</li>
                <li>Selected 2</li>
            </ul>
        </div>
    </div>
</template>

<script>
import Item from './components/Item.vue';

export default {
    name: 'App',
    components: {
        Item,
    },
    data() {
        return {
            itemsDataList: [],
            showPopup: false,
        };
    },
    created() {
        this.getItemsData();
    },
    methods: {
        getItemsData() {
            fetch('items.json')
                .then((response) => response.json())
                // eslint-disable-next-line no-return-assign
                .then((data) => (this.itemsDataList = data));
        },
    },
};
</script>

<style lang="scss">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

.banner {
    border-bottom: 1px solid grey;
    display: flex;
    padding-bottom: 0.5rem;
    width: 100%;

    &__select {
        padding-right: 2rem;
    }

    &__label {
        padding-left: 1.5rem;
    }
}

.table {
    border-collapse: collapse;
    width: 100%;

    &__row {
        border-bottom: 1px solid grey;
    }

    &__header,
    &__data {
        padding: 0.5rem 1rem;
        text-align: left;
    }

    &__data {
        &.-checkbox {
            padding: 0.5rem 0;
        }
    }
}
</style>
