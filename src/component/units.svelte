<script>
    export let data;
</script>

<div class="units-container">
    <div class="number-item big">
        <code>{data['coursework-hours'] ?? '--'}</code>
        <span>Units Earned</span>
    </div>
</div>


<style lang="scss">

    @import '../style/color.scss';
    @import '../style/frame.scss';

    .units-container {

        @include bignumber($theme-1: $theme-blue-700, $theme-2: $theme-gray-700, $weight: 800);

    }

</style>