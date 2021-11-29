<template>
    <tr class="table__row">
        <td class="table__data -checkbox">
            <input
                class="table__checkbox"
                type="checkbox"
                id="{{ item.name }}"
                name="{{ item.name }}"
                value="{{ item.name }}"
                :disabled="item.status !== 'available' ? true : false"
                @change="$emit('makeSelections', item);"
            >
        </td>
        <td class="table__data">
            <label class="table__label" for="{{ item.name }}">{{ item.name }}</label>
        </td>
        <td class="table__data">{{ item.device }}</td>
        <td class="table__data">{{ item.path }}</td>
        <td
            :class="['table__data', { '-is-available': item.status === 'available' }]"
        >
            {{ capitalize(item.status) }}
        </td>
    </tr>
</template>

<script>
export default {
    name: 'Item',
    props: ['item'],
    methods: {
        capitalize(str) {
            const capitalized = [];

            capitalized.push(str.charAt(0).toUpperCase() + str.slice(1).toLowerCase());

            return capitalized.join(' ');
        },
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
