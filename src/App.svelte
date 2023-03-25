<script>
 import { Loader } from '@googlemaps/js-api-loader';

 const topLeftLat = 50.8355246;
 const topLeftLong = -1.0938555;

 const bottomRightLat =  50.7834841;
 const bottomRightLong = -1.0392115;



 let map = null;

// let randPoint = {lat: topLeftLat, long: topLeftLong}

 const getrand = (min, max) =>  Math.random() * (max - min) + min;

 const getRandomPoint = (topLeftLat, bottomRightLat, topLeftLong, bottomRightLong) => {
     let lat = getrand(topLeftLat, bottomRightLat);
     let long = getrand(topLeftLong, bottomRightLong);
      let latLng = new google.maps.LatLng(lat, long); //Makes a latlng
      map.setCenter(latLng);
 }

 const constructLink = (point) => `https://www.google.com/maps/@${point.lat},${point.long},20z`

 const constructEmbed = (point) => `https://www.google.com/maps/embed?pb=!1m10!1m8!1m3!1d3085.1720377496626!2d${point.long}!3d${point.lat}!3m2!1i1024!2i768!4f13.1!5e0!3m2!1sen!2suk!4v1679748545620!5m2!1sen!2suk`




const apiOptions = {
apiKey: key,
};

    const loader = new Loader(apiOptions);

    loader.load().then(() => {
      console.log('Maps JS API Loaded');
      const mapOptions = {
      center: { lat: 50.806999, lng: -1.069369 },
      zoom: 20,
      mapTypeId: 'satellite'
   };

     const mapDiv = document.getElementById('map');
     map = new google.maps.Map(mapDiv, mapOptions);
     let latLng = new google.maps.LatLng(bottomRightLat, bottomRightLong); //Makes a latlng
     console.log(topLeftLat, topLeftLong);
//     map.setCenter(latLng);
     console.log("showing map");

//    clickroute(-123.6, 47.7, 9);
//map.setCenter(-123.6, 47.7, 9);
    });

</script>


<main>
    <h1>Random Point in Portsmouth</h1>


    <button on:click={() => getRandomPoint(topLeftLat, bottomRightLat, topLeftLong, bottomRightLong)}>
        generate new point
    </button>
    <p>
        <div id="map" style=" width: 50rem; height: 50rem;">A map</div>

</main>
