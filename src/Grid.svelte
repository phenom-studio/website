<div class="grid">
    <slot />
</div>

<style lang="scss">
    .grid {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      column-gap: 1rem;
    }
</style>