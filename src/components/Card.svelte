<script>
    export let project;

    let { title, tag } = project;
</script>

<div class="card">
    <div class="background">
        <div class="content">
            <h3>{title}</h3>
            <h4>{tag}</h4>
        </div>
    </div>
</div>

<style lang="scss">
    .background {
        position: relative;
        width: 100%;
        padding-bottom: 100%;
    }

    .card {
        width: 66vw;
        height: 33vw;
        margin: 0 auto;
        margin-top: 33vw;
        background-color: white;
    }

    .content {
        position: absolute;
    }
</style>