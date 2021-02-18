<script>
  export let carousel;
  export let i;
  let transitionDuration = 2000;
  let transitionDelay = 3000;

  function fade(node, {
      delay = 0,
      duration = 400
    }) {
      const o = +getComputedStyle(node).opacity;

      return {
        delay,
        duration,
        css: t => `opacity: ${t * o}`
      };
  }

  let index = 0;
  let run;

  const next = () =>
    index = (index + 1) % carousel.length

  $: {
    run = setInterval(next, transitionDelay);
  }

  if (i == 0 ) {
    transitionDelay = 5000;
  } else if (i == 1) {
    transitionDelay = 9000;
  } else if (i == 2) {
    transitionDelay = 7000;
  }

  setTimeout(next, transitionDelay);

</script>

  <div id="carousel-images">
    <!-- todo: if status code != 200, skip -->
    {#each [carousel[index]] as item (item.id)}  
      <figure on:click = {() => {console.log(i)}}>
        <img
          out:fade="{{ duration: 2000 }}"
          in:fade="{{ duration: 2000 }}"
          src = {item.path}
          alt = {item.alt}
        />
        <figcaption>{item.caption}</figcaption>
      </figure>
    {/each}
  </div>

<style>

  #carousel-images {
    position: relative;
    width: 33vw;
    height: 48vw;
  }

  figure, img {
    position: absolute;
    width: 100%;
    height: 48vw;
  }

  figure {
    margin-block-start: 0;
    margin-block-end: 0;
    margin-inline-start: 0;
    margin-inline-end: 0;
  }

  figcaption {
    position: relative;
    top: -40px;
    color: white;
  }

  </style>