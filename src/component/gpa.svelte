<script>
    export let data;

    let expanded = false;

</script>

<div class={`gpa-container ${expanded && 'expanded'}`}>
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
        {#if expanded}
            <div class="number-item low">
                <code>{data['prep'] ?? '--'}</code>
                <span>Premajor</span>
            </div>
            <div class="number-item low">
                <code>{data['ge'] ?? '--'}</code>
                <span>Gen Ed</span>
            </div>
        {/if}
    </div>
    <button class="small" on:click={() => expanded = !expanded}>{expanded ? 'x' : '+'}</button>
</div>

<style lang="scss">

    @import '../style/color.scss';
    @import '../style/frame.scss';

    .gpa-container {

        @include bignumber($theme-1: $theme-blue-500, $theme-2: $theme-gray-700);

        align-self: flex-start;
        &:hover {
            .low { display: flex; }
            > button { opacity: 1; }
        }

        transition: height 0.3s ease;
        position: relative;

        > button {
            opacity: 0;
            position: absolute;
            right: 0.5rem;
            bottom: -0.75rem;
            transition: all 0.1s ease;
            background: white;
            border: solid 1px $theme-gray-200;
            &:hover {
                border: solid 1px $theme-gray-400;
            }
            &:active {
                background: $theme-gray-100;
            }
        }
    }

</style>