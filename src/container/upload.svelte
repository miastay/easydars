<script>

    let files;
    let html = null;

    export let updateAudit;

    $: if (files && !html) {
        let reader = new FileReader();
        reader.onload = function() {
            html = fromHTML(reader.result);
            console.log(html)
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
        const result = template.content.children;

        // Then return either an HTMLElement or HTMLCollection,
        // based on whether the input HTML had one or more roots.
        if (result.length === 1) return result[0];
        return result;
    }

    function x() {
        let hiddenDiv = document.querySelector('#originalAudit')
        for(let obj of html) {
            console.log(obj)
            hiddenDiv.appendChild(obj)
        }
        updateAudit(html)
    }
    
</script>
    
<div id="container">
    <div class="header">
        <h1>easydars</h1>
    </div>
    <input bind:files type="file" accept=".html,.htm"/>
    <button on:click={() => x()}>audit result</button>
    <div id="originalAudit"></div>
</div>
    
    
<style lang="scss">
    #container {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    #originalAudit {
        display: none;
    }
</style>