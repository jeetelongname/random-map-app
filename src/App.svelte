<script>
 const topLeftLat = 50.8364233
 const topLeftLong = -1.0944622

 const bottomRightLat =  50.7931739
 const bottomRightLong = -1.06503

 let randPoint = {lat: topLeftLat, long: topLeftLong}

 const getrand = (min, max) =>  Math.random() * (max - min) + min;

 const getRandomPoint = (topLeftLat, bottomRightLat, topLeftLong, bottomRightLong) => {
   randPoint = {lat: getrand(topLeftLat, bottomRightLat), long: getrand(topLeftLong, bottomRightLong)}
 }

 const constructLink = (point) => `https://www.google.com/maps/@${point.lat},${point.long},20z`

</script>


<main>
  <h1>Random Point in Portsmouth</h1>

  <p>{constructLink(randPoint)}</p>
  <button on:click={() => getRandomPoint(topLeftLat, bottomRightLat, topLeftLong, bottomRightLong)}>
      google link: <a href="{constructLink(randPoint)}">Click here</a>
  </button>
</main>
