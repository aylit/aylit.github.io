<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Character Map</title>
    <link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
    <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js"></script>
    <style>
        #map { height: 500px; width: 100%; }
    </style>
</head>
<body>

    <h2>Character Locations</h2>
    <div id="map"></div>

    <script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
    <script>
        // Initialize Supabase (Replace with your Supabase URL and API Key)
        const SUPABASE_URL = "YOUR_SUPABASE_URL";
        const SUPABASE_KEY = "YOUR_ANON_PUBLIC_KEY";
        const supabase = supabase.createClient(SUPABASE_URL, SUPABASE_KEY);

        // Initialize the map
        var map = L.map('map').setView([42.3601, -71.0589], 3);

        // Add OpenStreetMap tile layer
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; OpenStreetMap contributors'
        }).addTo(map);

        let markers = {};

        // Function to load characters
        async function loadMarkers() {
            let { data: characters, error } = await supabase.from('characters').select('*');
            if (error) console.error(error);
            characters.forEach(char => addMarker(char));
        }

        // Function to add a marker
        function addMarker(char) {
            let marker = L.marker([char.lat, char.lon], { draggable: true }).addTo(map)
                .bindPopup(`<b>${char.name}</b> - Drag to move`);

            markers[char.id] = marker;

            // Update database on drag
            marker.on("dragend", async function (e) {
                let newLatLng = e.target.getLatLng();
                await supabase.from('characters').update({
                    lat: newLatLng.lat,
                    lon: newLatLng.lng
                }).eq('id', char.id);
            });
        }

        // Listen for database updates
        supabase.channel('characters')
            .on('postgres_changes', { event: '*', schema: 'public', table: 'characters' }, payload => {
                let char = payload.new;
                if (markers[char.id]) {
                    markers[char.id].setLatLng([char.lat, char.lon]);
                } else {
                    addMarker(char);
                }
            })
            .subscribe();

        // Load markers on start
        loadMarkers();
    </script>
</body>
</html>
