<script>
    export let project;

    let { title, tag } = project;
</script>

<div class="card">
    <div class="background">
        <h3>{title}</h3>
        <h4>{tag}</h4>
    </div>
</div>

<style lang="scss">
    .background {
        width: 100%;
        background-color: rebeccapurple;
    }
</style>