<template>
    <tr class="table__row">
        <td class="table__data -checkbox">
            <input class="table__checkbox" type="checkbox" id="smss" name="smss" checked>
        </td>
        <td class="table__data">
            <label class="table__label" for="smss">smss.exe</label>
        </td>
        <td class="table__data">Stark</td>
        <td class="table__data">\\Device\\HarddiskVolume2\\Windows\\System32\\smss.exe</td>
        <td class="table__data">scheduled</td>
    </tr>
</template>

<script>
export default {
    name: 'Item',
    props: ['item'],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
