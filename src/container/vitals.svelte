<script>
    import { onMount } from 'svelte';
    import Gpa from '../component/gpa.svelte';
    import Units from '../component/units.svelte';
    import Completion from '../component/completion.svelte';

    let vitals = {};
    export let audit;

    $: (audit && document) && generateVitals(audit)

    function generateVitals(aud) {
        console.log(aud)
        let gpaStrings = document.querySelectorAll('.graphGPALabel')

        vitals.gpa = {
            'overall': gpaStrings[3].innerText,
            'major': gpaStrings[1].innerText,
            'upperdiv': gpaStrings[2].innerText,
            'ge': gpaStrings[0].innerText
        }

        let hours = document.querySelector('.rname_UCLACWK')
        let coursework_hours = hours.querySelector('.hours').innerText
        vitals.units = {
            'coursework-hours': coursework_hours
        }

        let subreqs = document.querySelectorAll('.subreqPretext')
        let totalSubReqs = subreqs.length;
        let incompleteSubReqs = 0;
        for(let sub of subreqs) {
            if(sub.querySelector('.Status_NO')) incompleteSubReqs++;
        }

        vitals.subreqs = {
            'total': totalSubReqs,
            'incomplete': incompleteSubReqs
        }

    }

</script>

<div class="vitals">
    {#if vitals?.gpa}
        <Gpa data={vitals.gpa} />
    {/if}
    {#if vitals?.units}
        <Units data={vitals.units} />
    {/if}
    {#if vitals?.subreqs}
        <Completion data={vitals.subreqs} />
    {/if}
</div>

<style>
    .vitals {
        display: flex;
        flex-direction: row;
        gap: 1rem;
    }
</style>