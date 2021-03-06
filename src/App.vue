<template>
    <div class="banner">
        <div class="banner__select">
            <input
                class="banner__checkbox"
                type="checkbox"
                id="selected"
                name="selected"
            >
            <label
                v-if="selectedItems.length > 0"
                class="banner__label"
                for="selected"
            >
                Selected {{ selectedItems.length }}
            </label>
            <label v-else class="banner__label" for="selected">None Selected</label>
        </div>
        <button
            class="banner__button"
            @click="showPopup = true"
            :disabled="selectedItems.length === 0 ? true : false"
        >
            Download Selected
        </button>
    </div>
    <table class="table">
        <thead class="table__head">
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
                @makeSelections="selectItems(item)"
            />
        </tbody>
    </table>
    <div v-if="showPopup" class="popup__overlay">
        <div class="popup">
            <button class="popup__close" @click="showPopup = false">
                <span class="sr-only">Close</span>
            </button>
            <ul class="popup__list">
                <li
                    v-for="item in this.selectedItems"
                    :key="item.name"
                    class="popup__item"
                >
                    {{ item.device }} - {{ item.path }}
                </li>
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
            selectedItems: [],
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
        selectItems(item) {
            if (this.selectedItems.indexOf(item) === - 1) {
                this.selectedItems.push(item);
            } else {
                this.selectedItems.splice(this.selectedItems.indexOf(item), 1);
            }
        },
    },
};

// Background of table row needs to change on:
// 2. when row checkbox is checked
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

    &__button {
        background: none;
        border: none;
        cursor: pointer;
        font-family: inherit;
        font-size: 1rem;

        &:disabled {
            cursor: not-allowed;
        }
    }
}

.table {
    $scope: &;

    border-collapse: collapse;
    width: 100%;

    &__row {
        border-bottom: 1px solid grey;

        &:hover {
            background-color: rgba(0, 0, 0, 0.1);
        }
    }

    &__head {
        #{$scope}__row {
            &:hover {
                background: none;
            }
        }
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

        &.-is-available {
            position: relative;

            &::before {
                background-color: green;
                border-radius: 50%;
                content: '';
                height: 1rem;
                left: -1rem;
                position: absolute;
                top: 50%;
                transform: translateY(-50%);
                width: 1rem;
            }
        }
    }
}

.popup {
    background-color: white;
    border-radius: 2rem;
    left: 50%;
    max-width: 40rem;
    padding: 5rem 0;
    position: absolute;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 90%;
    z-index: 2;

    &__overlay {
        align-items: flex-start;
        background-color: rgba(0, 0, 0, 0.5);
        bottom: 0;
        display: flex;
        justify-content: center;
        left: 0;
        overflow: scroll;
        padding: 2rem;
        position: fixed;
        right: 0;
        top: 0;
        z-index: 100;
    }

    &__close {
        background-color: white;
        border: 1px solid grey;
        border-radius: 50%;
        padding: 1.5rem;
        position: absolute;
        right: -1rem;
        top: -1rem;

        &:hover,
        &:focus,
        &:active {
            background-color: black;
            color: white;
        }
    }

    &__list {
        list-style-type: none;
    }

    &__item {
        padding-right: 4.5rem;
        text-align: left;
    }
}
</style>
