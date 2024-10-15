<!-- src/lib/Map.svelte -->
<script>
    import { onMount } from 'svelte';
    import 'leaflet/dist/leaflet.css';

    let map;

    onMount(() => {
        // Ensure that this runs only in the browser
        if (typeof window !== 'undefined') {
            // Initialize the map
            map = L.map('map').setView([51.505, -0.09], 13);

            // Add tile layer
            L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
                attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
            }).addTo(map);

            // Add a marker
            L.marker([51.5, -0.09]).addTo(map).bindPopup('A pretty CSS3 popup.<br> Easily customizable.').openPopup();
        }
    });
</script>

<div id="map"></div>

<style>
    #map {
        width: 100%;
        height: 700px;
    }
</style>
