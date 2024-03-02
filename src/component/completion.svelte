<script>
    export let data;
</script>

<div class="completion-container">
    <div class="number-item big">
        <code class="sup">{`${data['incomplete']}` ?? '--'}<code>{`/${data['total']}`}</code></code>
        <span>Remaining</span>
    </div>
</div>


<style lang="scss">

    @import '../style/color.scss';
    @import '../style/frame.scss';

    .completion-container {

        @include bignumber($theme-1: $theme-blue-600, $theme-2: $theme-gray-700, $weight: 800);

        .sup {
            display: flex;
            > code {
                font-size: 1.5rem !important;
                align-self: flex-start;
                color: $theme-gray-300;
                line-height: 1.5rem !important;
                align-self: baseline !important;
            }
        }

    }

</style>