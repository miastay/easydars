<script>
    import { onMount } from 'svelte';


    let files;
    let html = null;
    let osSaveString = "Ctrl + S"

    export let updateAudit;

    $: if (files && !html) {
        let reader = new FileReader();
        reader.onload = function() {
            html = fromHTML(reader.result);
            console.log(html)
            updateAudit(html);
        };
        reader.readAsText(files[0]);
    }

    function fromHTML(html, trim = true) {
        // Process the HTML string.
        html = trim ? html.trim() : html;
        if (!html) return null;

        // Then set up a new template element.
        const template = document.createElement('template');
        template.innerHTML = html;
        const result = Array.from(template.content.children).filter((x) => x.tagName !== "LINK");

        console.log(result)
        // Then return either an HTMLElement or HTMLCollection,
        // based on whether the input HTML had one or more roots.
        if (result.length === 1) return result[0];
        return result;
    }

    onMount(() => {
        let os = window.navigator.oscpu;
        if(os.includes('MacOS')) osSaveString = "Cmd + S"
        else osSaveString = "Ctrl + S"
    })

</script>
    
<div class="container">
    <div class="header">
        <h1>easydars</h1>
    </div>
    <div class="steps">
        <div class="step 1">
            <h2>1</h2>
            <span>Go to <a href="https://dars.ucla.edu" target="_blank" rel="noopener noreferrer">dars.ucla.edu</a> and run a new DARS audit</span>
        </div>
        <div class="step 2">
            <h2>2</h2>
            <span>Open the new audit and save the page as an HTML file {`(${osSaveString})`}</span>
        </div>
        <div class="step 3">
            <h2>3</h2>
            <span>Upload the HTML file here &rarr;</span>
            <input id="auditUpload" bind:files type="file" accept=".html,.htm"/>
        </div>
    </div>
</div>
    
    
<style lang="scss">

    @import '../style/frame.scss';
    @import '../style/color.scss';
    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 1rem;
        .steps {
            display: flex;
            flex-direction: column;
            gap: 2rem;
            .step {
                @include frame;
                padding: 1rem 2rem;
                flex-direction: row;
                align-items: center;
                gap: 2rem;
                width: unset !important;
            }
        }
    }
    #auditUpload {
        background: $theme-gray-100;
        padding: 0.5rem;
    }
</style>