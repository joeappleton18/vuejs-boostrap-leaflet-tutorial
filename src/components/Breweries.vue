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
            <div class="col-6">
                <BreweriesList  :brew-list="breweries"/>
            </div>
            <!-- /.col-6 -->
            <div class="col-6">
                <BreweriesMap  :brew-list="breweries" />
            </div>
            <!-- /.col-6 -->
        </div>
        <!-- /.row -->


    </div>


</template>

<script>

    import axios from 'axios';
    import BreweriesList from './BreweriesList';
    import BreweriesMap   from './BreweriesMap';

    export default {
        name: 'Breweries',
        components: {BreweriesList, BreweriesMap},
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




</style>
