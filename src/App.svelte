<script>
  import { Loader } from "@googlemaps/js-api-loader";

  const topLeftLat = 50.8355246;
  const topLeftLong = -1.0938555;

  const bottomRightLat = 50.7834841;
  const bottomRightLong = -1.0392115;
  let map = null;
  let geocoder = null;
  let latLng = null;

  const getrand = (min, max) => Math.random() * (max - min) + min;

  const getRandomPoint = (
    topLeftLat,
    bottomRightLat,
    topLeftLong,
    bottomRightLong
  ) => {
    document.querySelector(".place").textContent = "";
    let lat = getrand(topLeftLat, bottomRightLat);
    let long = getrand(topLeftLong, bottomRightLong);
    latLng = new google.maps.LatLng(lat, long); //Makes a latlng
    map.setZoom(20);
    map.setCenter(latLng);
  };

  const revealLocation = (latLng) => {
    if (document.querySelector(".place").textContent == "") {
      geocoder.geocode({ location: latLng }).then((response) => {
        if (response.results[0]) {
          document.querySelector(".place").textContent =
            response.results[0].formatted_address;
        }
      });
    }
  };

  const apiOptions = {
    apiKey: null,
  };

  const loader = new Loader(apiOptions);

  loader.load().then(() => {
    console.log("Maps JS API Loaded");
    const mapOptions = {
      center: { lat: 50.806999, lng: -1.069369 },
      zoom: 13,
      mapTypeId: "satellite",
    };

    const mapDiv = document.getElementById("map");
    map = new google.maps.Map(mapDiv, mapOptions);
    geocoder = new google.maps.Geocoder();
    let latLng = new google.maps.LatLng(bottomRightLat, bottomRightLong); //Makes a latlng
  });
</script>

<main>
  <h1>Random Point in Portsmouth</h1>

  <button on:click={() => getRandomPoint(topLeftLat, bottomRightLat, topLeftLong, bottomRightLong)}>
    generate new point
  </button>

  <button on:click={() => revealLocation(latLng)}> Show location </button>

  <div id="map" style=" width: 50rem; height: 50rem;">A map</div>
  <div class="place">''</div>
</main>

<style>
</style>
