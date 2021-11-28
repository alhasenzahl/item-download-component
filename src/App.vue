<template>
    <div class="banner">
        <div class="banner__select">
            <input class="banner__checkbox" type="checkbox" id="selected" name="selected" checked>
            <label class="banner__label" for="selected">Selected 2</label>
        </div>
        <button class="banner__button">Download Selected</button>
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
            <tr class="table__row">
                <td class="table__data -checkbox">
                    <input class="table__checkbox" type="checkbox" id="netsh" name="netsh" checked>
                </td>
                <td class="table__data">
                    <label class="table__label" for="netsh">netsh.exe</label>
                </td>
                <td class="table__data">Targaryen</td>
                <td class="table__data">\\Device\\HarddiskVolume2\\Windows\\System32\\netsh.exe</td>
                <td class="table__data">available</td>
            </tr>
            <tr class="table__row">
                <td class="table__data -checkbox">
                    <input class="table__checkbox" type="checkbox" id="uxtheme" name="uxtheme">
                </td>
                <td class="table__data">
                    <label class="table__label" for="uxtheme">uxtheme.dll</label>
                </td>
                <td class="table__data">Lanniester</td>
                <td class="table__data">\\Device\\HarddiskVol\\Windows\\System32\\uxtheme.dll</td>
                <td class="table__data">available</td>
            </tr>
            <tr class="table__row">
                <td class="table__data -checkbox">
                    <input class="table__checkbox" type="checkbox" id="cryptbase" name="cryptbase">
                </td>
                <td class="table__data">
                    <label class="table__label" for="cryptbase">cryptbase.dll</label>
                </td>
                <td class="table__data">Martell</td>
                <td class="table__data">\\Device\\HarddiskVol\\Windows\\System32\\cryptbase.dll</td>
                <td class="table__data">scheduled</td>
            </tr>
            <tr class="table__row">
                <td class="table__data -checkbox">
                    <input class="table__checkbox" type="checkbox" id="7za" name="7za" checked>
                </td>
                <td class="table__data">
                    <label class="table__label" for="7za">7za.exe</label>
                </td>
                <td class="table__data">Baratheon</td>
                <td class="table__data">\\Device\\HarddiskVolume1\\temp\\7za.exe</td>
                <td class="table__data">scheduled</td>
            </tr>
        </tbody>
    </table>
</template>

<script>

export default {
    name: 'App',
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
