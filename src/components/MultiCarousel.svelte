<script>
  import Carousel from 'Carousel.svelte'

  export let carouselImages;

</script>

{#each carouselImages as carousel, i}
    <Carousel 
        {carousel}
        {i}
    />
{/each}

<style>

</style>