<script>
    export let data;
</script>

<div class="units-container">
    <div class="number-item big">
        <code>{data['total'] ?? '--'}</code>
        <span>Units Earned</span>
    </div>
    <div class="number-small-container">
        <div class="number-item">
            <code>{data['ucla'] ?? '--'}</code>
            <span>UCLA</span>
        </div>
        <div class="number-item">
            <code>{data['ap'] ?? '--'}</code>
            <span>AP</span>
        </div>
    </div>
</div>


<style lang="scss">

    @import '../style/color.scss';
    @import '../style/frame.scss';

    .units-container {

        @include bignumber($theme-1: $theme-blue-700, $theme-2: $theme-gray-700, $weight: 800);

    }

</style>