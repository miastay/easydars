<script>
    import Upload from './upload.svelte';
    import Vitals from './vitals.svelte';

    let audit;
    function updateAudit(aud) {
        audit = aud;
    }

</script>


<div>
    <Upload updateAudit={updateAudit}/>
    <Vitals audit={audit}/>
</div>