<template>
    <div class="card">
        <ul class="list-group list-group-flush brew-list">
            <li @mouseover="mouseOver(index)"
                @mouseleave="mouseLeave(index)"

                :key="index"
                v-for="(brew, index) in brewList"
                class="list-group-item ">

                {{brew.name}}, {{brew.state}}

            </li>

        </ul>
    </div>
</template>

<script>
    export default {
        name: "BreweriesList",
        props: ['brewList'],
        methods: {
            mouseOver: function (index) {
                this.$emit('mouse-over-brew', index);
            },
            mouseLeave: function (index) {
                this.$emit('mouse-left-brew', index);
            }
        }
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
