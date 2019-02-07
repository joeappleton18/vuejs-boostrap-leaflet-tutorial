<template>

    <div class="row map">
        <!-- <h2> Zoom {{currentZoom}}  Center {{currentCenter}}</h2>-->
        <l-map @update:zoom="zoomUpdate" @update:center="centerUpdate"  :zoom="zoom" :center="center">
            <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
            <l-marker :key="index" v-for="(brew,index) in brewList"
                      :lat-lng="latLng(brew.latitude, brew.longitude)"></l-marker>
        </l-map>


    </div>
    <!-- /.row map -->


</template>

<script>
    import {LMap, LTileLayer, LMarker} from 'vue2-leaflet';

    export default {
        name: "BreweriesMap",
        props: ['brewList'],
        data: function () {
            return {
                center: L.latLng(33.683295, -111.930685),
                url: 'https://tile.thunderforest.com/transport/{z}/{x}/{y}.png?apikey=e955b6c9bc0b4ec6a38495e3f90d87b5',
                attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
                marker: L.latLng(47.413220, -1.219482),
                zoom: 7,
                currentCenter: L.latLng(47.413220, -1.219482),
                currentZoom: 7
            }
        },
        components: {
            LMap,
            LTileLayer,
            LMarker
        }, methods: {

            latLng: function (lat, lng) {

                return L.latLng(lat, lng);

            },

            centerUpdate: function(center) {
                this.currentCenter = center;
            },
            zoomUpdate: function(zoom) {
               this.currentZoom = zoom;
            },
        }
    }
</script>

<style type="scss" scoped>


    .map {
        height: 100vh;
    }

</style>
