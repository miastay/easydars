<script>
    export let data;
</script>

<div class="gpa-container">
    <div class="number-item big">
        <code>{data['overall'] ?? '--'}</code>
        <span>Overall GPA</span>
    </div>
    <div class="number-small-container">
        <div class="number-item">
            <code>{data['major'] ?? '--'}</code>
            <span>Major</span>
        </div>
        <div class="number-item">
            <code>{data['upperdiv'] ?? '--'}</code>
            <span>Upper Division</span>
        </div>
    </div>
</div>

<style lang="scss">

    @import '../style/color.scss';
    @import '../style/frame.scss';

    .gpa-container {
        @include bignumber($theme-1: $theme-blue-500, $theme-2: $theme-gray-700);
    }

</style>