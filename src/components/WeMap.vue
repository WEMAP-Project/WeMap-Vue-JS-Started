<template>

</template>

<script>

import {
    defineProps,
    reactive
} from 'vue'

defineProps({
    msg: String
})

const state = reactive({
    count: 0
})

export default {
    name: "Map",
    metaInfo: {
        title: "WeMap",
    },

    mounted: function () {
        // let wemapgl = document.createElement('script');
        // wemapgl.setAttribute('src', "wemap-gl.js");
        // document.head.appendChild(wemapgl);
    },

    created() {
        this.init();
    },

    methods: {
        init() {
            this.wemapgl = new wemapgl.WeMap({
                container: "app",
                key: "vpstPRxkBBTLaZkOaCfAHlqXtCR",
                style: "bright",
                center: [105.1, 21.0],
                zoom: 13,
                // Turn on urlController
                urlController: true,
                // Turn on reverse
                reverse: true,
                // Turn on traffic
                traffic: false,
            });

            // Create Geocode control 
            let wemapControl = new wemapgl.WeGeocoder({
                flyTo: 'hybrid',
                key: 'vpstPRxkBBTLaZkOaCfAHlqXtCR',
                engine: 'default',
                suggestion: {
                    min_char: 4
                }
            });
            // Geocode control
            this.wemapgl.addControl(wemapControl);

            // Add Navigation control
            this.wemapgl.addControl(new wemapgl.NavigationControl(),  'bottom-right');

            // Geolocate control
            const geolocate = new wemapgl.WeGeolocateControl({
                positionOptions: {
                    enableHighAccuracy: true
                },
                trackUserLocation: true
            });
            // Add Geolocate control
            this.wemapgl.addControl(geolocate, 'bottom-right');

            // WeDirections
            let weMapDirections =  new wemapgl.WeDirections({
                key: "vpstPRxkBBTLaZkOaCfAHlqXtCR",
                supports: [
                    'engine02/driving',
                    'engine02/public-transport',
                    'engine02/walking',
                    'engine02/cycling',
                ],
                alternatives: true,
                geocoder: {
                    engine: 'pelias',
                }
            });
            this.wemapgl.addControl(weMapDirections, 'top-left');
        }
    }

}
</script>
