<script>
    import Controls from '../component/controls.svelte';
    import Incomplete from './incomplete.svelte';
    import Header from './header.svelte';
    import Upload from './upload.svelte';
    import Vitals from './vitals.svelte';

    let audit;
    function updateAudit(aud) {
        audit = aud;
        let hiddenDiv = document.querySelector('#originalAudit')
        for(let obj of aud) {
            console.log(obj)
            hiddenDiv.appendChild(obj)
        }
    }

    function newAudit() {
        audit = null;
        document.querySelector('#originalAudit').innerHTML = "";
    }

</script>

<div class="main">
    {#if !audit}
    <div class="content center">
        <Upload updateAudit={updateAudit}/>
    </div>
    {/if}
    {#if audit}
        <div class="content">
            <Header newAudit={newAudit}/>
            <Vitals audit={audit}/>
            <Controls />
        </div>
        <Incomplete />
    {/if}
</div>
<div id="originalAudit"></div>

<style lang="scss">

    .main { 
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    #originalAudit {
        display: none;
    }

    .content {
        display: flex;
        flex-direction: row;
        gap: 1rem;
        &.center {
            justify-content: center;
        }
    }

</style>