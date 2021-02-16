<script>
  import { fade } from 'svelte/transition';
  import { flip } from 'svelte/animate'
  export let carouselImages;
  export let imageWidth = 200;
  export let imageHeight = 300;
  export let transitionDuration = 2000;
  export let transitionDelay = 2000;

  let index = 0;
  let run;

  const next = () =>
    index = (index + 1) % carouselImages.length

  // const flipImageArray = () => {
  //   images = [...images.slice(1, images.length), images[0]]
  // }

  // const startAutoPlay = () => {
  //     interval = setInterval(rotateLeft, autoplaySpeed)
  // }

  // const stopAutoPlay = () => {
  //   clearInterval(interval)
  // }

  $: {
    run = setInterval(next, transitionDelay);
  }

  setTimeout(() => {next()}, 2000);

</script>

  <div id="carousel-images">
    <!-- {#each images as image (image.id)}
      <img
        src={image.path}
        alt={image.alt}
        style={`width: ${imageWidth}px; height: ${imageHeight}px`}
        animate:flip
      />
    {/each} -->
    {#each [carouselImages[index][index].path] as src (index)}
        <img
          transition:fade
          {src}
          style={`width: ${imageWidth}px; height: ${imageHeight}px`}
        />
    {/each}
  </div>

<style>
  #carousel-images {
    width: 200px;
  }

  img {
    position: absolute;
  }
  </style>