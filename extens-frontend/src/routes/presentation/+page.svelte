


<svelte:head>
	<title>Presentation</title>
	<meta name="description" content="Power point" />
</svelte:head>


<script>
    import {page, image} from "../../stores/swipe"
    $image = [
        "https://cdn.britannica.com/09/93509-050-4F6AD522/waterfront-tourists-Mauritius-Port-Louis.jpg",
        "https://dynamic-media-cdn.tripadvisor.com/media/photo-o/1a/5d/eb/8b/caption.jpg?w=600&h=400&s=1",
        "https://content.r9cdn.net/rimg/dimg/6d/95/fcbf92ce-city-13491-1671771f886.jpg?crop=true&width=1020&height=498",
    ];

</script>
<div
    class="body" 
   
    
>
    <!-- svelte-ignore a11y-img-redundant-alt -->
    <div class = "box"><img class = "image" src={$image[$page]} alt="Domage pas d'image" /></div>
    <p>Diapo : {$page}</p>
</div>

<style>
    .image{
        display: flex;
        justify-content: center;
        max-width: 80vw;
        min-width: 80vw;
        max-height: 100vh /7;

    }
    .body{
        width: 100%;
        height: 100%;
    }
</style>