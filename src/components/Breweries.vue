<template>
    <div class="container">

        <div class="row">
            <div class="col-12">
                <h1 class="text-center text-info">Breweries List</h1>
            </div>
            <!-- /.col-12 -->
        </div>
        <!-- /.row -->
        <div class="row">
            <div class="col-6 brew-list">
                <div class="card">
                    <ul class="list-group list-group-flush">
                        <li v-bind:key="index" v-for="(brew, index) in breweries" class="list-group-item  brew-item">
                            {{brew.name}}, {{brew.state}}
                        </li>

                    </ul>
                </div>
            </div>
            <!-- /.col-6 -->
            <div class="col-6">

            </div>
            <!-- /.col-6 -->
        </div>
        <!-- /.row -->


    </div>


</template>

<script>

    import axios from 'axios';

    export default {
        name: 'Breweries',
        data: function () {
            return {
                breweries: []
            }
        },

        mounted: function () {
            axios.get('https://api.openbrewerydb.org/breweries').then(r => {
                this.breweries = r.data;
            })
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

    .brew-list {
        overflow-y: scroll;
        height: 95vh;
        .brew-item {
            &:hover {
                background-color: darkgrey;
            }

        }
    }

</style>
