<script>
    export let data;
</script>

<div class="completion-container">
    <div class="number-item big">
        <code class="sup">{`${data['incomplete'] + data['in-progress']}` ?? '--'}<code>{`/${data['total']}`}</code></code>
        <span>Remaining</span>
    </div>
    <div class="number-small-container">
        <div class="number-item">
            <code>{data['in-progress'] ?? '--'}</code>
            <span>In Progress</span>
        </div>
        <div class="number-item">
            <code>{data['incomplete'] ?? '--'}</code>
            <span>Not Started</span>
        </div>
    </div>
</div>


<style lang="scss">

    @import '../style/color.scss';
    @import '../style/frame.scss';

    .completion-container {

        @include bignumber($theme-1: $theme-blue-600, $theme-2: $theme-gray-700, $weight: 800);

        width: unset !important;

        .sup {
            display: flex;
            > code {
                white-space: nowrap;
                font-size: 1.5rem !important;
                align-self: flex-start;
                color: $theme-gray-300;
                line-height: 1.5rem !important;
                align-self: baseline !important;
            }
        }

    }

</style>