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

 const constructEmbed = (point) => `https://www.google.com/maps/embed?pb=!1m10!1m8!1m3!1d3085.1720377496626!2d${point.long}!3d${point.lat}!3m2!1i1024!2i768!4f13.1!5e0!3m2!1sen!2suk!4v1679748545620!5m2!1sen!2suk`
</script>


<main>
    <h1>Random Point in Portsmouth</h1>

    <iframe
        title="A map"
        src={constructEmbed(randPoint)}
        width="600"
        height="450"
        style="border:0;"
        allowfullscreen=""
        loading="lazy"
        referrerpolicy="no-referrer-when-downgrade">
    </iframe>

    <button on:click={() => getRandomPoint(topLeftLat, bottomRightLat, topLeftLong, bottomRightLong)}>
        generate new point
    </button>
    <p>
        google link: <a href="{constructLink(randPoint)}">{constructLink(randPoint)}</a>
    </p>

</main>
