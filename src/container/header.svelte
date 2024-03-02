<script>

    export let newAudit;

</script>

<div class="header" on:click={() => newAudit()} aria-roledescription="reset button">
    <h1>easydars</h1>
</div>

<style lang="scss">

    @import '../style/color.scss';

    :hover {
        cursor: pointer;
    }

    .header {
        padding: 1rem;
        background: $theme-blue-600;
        border: solid 1px $theme-blue-700;
        display: grid;
        h1 {
            margin-block: 0;
            justify-self: center;
            align-self: center;
            margin-bottom: 0.5rem;
            color: white;
        }
    }
</style>