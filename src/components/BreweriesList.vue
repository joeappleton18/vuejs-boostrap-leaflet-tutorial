<template>
    <div class="card">
        <ul class="list-group list-group-flush brew-list">
            <li v-bind:key="index"
                v-for="(brew, index) in brewList" class="list-group-item ">
                {{brew.name}}, {{brew.state}}
            </li>

        </ul>
    </div>
</template>

<script>
    export default {
        name: "BreweriesList",
        props: ['brewList']
    }
</script>

<style lang="scss" scoped>

    .brew-list {
        overflow-y: scroll;
        height: 95vh;
        li {
            &:hover {
                background-color: darkgrey;
            }

        }
    }
</style>
