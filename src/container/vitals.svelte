<script>
    import { onMount } from 'svelte';
    import Gpa from '../component/gpa.svelte';
    import Units from '../component/units.svelte';
    import Completion from '../component/completion.svelte';
    import Program from '../component/program.svelte';

    let vitals = {};
    export let audit;

    $: (audit && document) && generateVitals(audit)

    function generateVitals(aud) {
        console.log(aud)

        let gpaStrings = document.querySelectorAll('.graphGPALabel')
        let prep = document.querySelector("*[rname$='-PREP']")
        let prepGPA = "--"
        if(prep) prepGPA = prep.querySelector('.gpa.number')

        vitals.gpa = {
            'overall': gpaStrings[3].innerText,
            'major': gpaStrings[1].innerText,
            'upperdiv': gpaStrings[2].innerText,
            'ge': gpaStrings[0].innerText,
            'prep': prepGPA.innerText
        }

        let units = document.querySelector("*[rname='MIN 180']") 
        let hours = units.querySelectorAll('.hours.number')
        vitals.units = {
            'total': hours[0].innerText,
            'ucla': hours[2].innerText,
            'ap': hours[4].innerText,
        }

        let subreqs = document.querySelectorAll('.subreqPretext')
        let totalSubReqs = subreqs.length;
        let incompleteSubReqs = 0;
        let inprogressSubReqs = 0;
        for(let sub of subreqs) {
            if(sub.querySelector('.Status_NO')) incompleteSubReqs++;
            if(sub.querySelector('.Status_IP')) inprogressSubReqs++;
        }

        vitals.subreqs = {
            'total': totalSubReqs,
            'incomplete': incompleteSubReqs,
            'in-progress': inprogressSubReqs
        }

        let meta = document.querySelector('.tabular.cleared.resultList')
        let programName = meta.querySelector('td:last-child').innerText.trim();
        vitals.program = {
            'program-name': programName,
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
    {#if vitals?.program}
        <Program data={vitals.program} />
    {/if}
</div>

<style>
    .vitals {
        display: flex;
        flex-direction: row;
        flex-grow: 1 0;
        flex-shrink: 1;
        gap: 1rem;
    }
</style>