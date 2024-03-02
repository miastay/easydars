<script>
    export let data;
</script>

<div class="program-container">
    <div class="number-item big">
        <code>{data['program-name'] ?? '--'}</code>
        <span>Program</span>
    </div>
</div>


<style lang="scss">

    @import '../style/color.scss';
    @import '../style/frame.scss';

    .program-container {

        @include bignumber($theme-1: $theme-blue-700, $theme-2: $theme-gray-700, $weight: 800);

        width: unset;

        .number-item > code {
            font-size: 2rem !important;
            line-height: 1.75rem !important;
            text-align: right;
        }

    }

</style>