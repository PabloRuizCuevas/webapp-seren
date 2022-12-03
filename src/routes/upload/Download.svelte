
<script lang="ts">
    import { fade } from 'svelte/transition';
    let root_ip: string = 'http://127.0.0.1:8000';
   
    async function getReportStatus() {
        /* Download report if exist  */
        console.log('reports-status')
        console.log('is failing here?')
        const status = await fetch(`${root_ip}/get-report-status`, {
            method: 'GET'
        });
        const text = await status.text();

        if (status.ok) {
            return text;
        } else {
            throw new Error(text);
        }
    }
    let report_status = getReportStatus()

    async function getReport(endPoint: string) {
        /* Download report if exist  */
        console.log('reports')
        const formData = new FormData();
        formData.append('name', 'file.name');
        const download = fetch(`${root_ip}/${endPoint}`, {
            method: 'POST'
        })
        .then(response => response.blob())
        .then(blob => {
            var url = window.URL.createObjectURL(blob);
            var a = document.createElement('a');
            a.href = url;
            a.download = "Report.xlsx";
            document.body.appendChild(a);
            a.click();    
            a.remove();      
        });
    } 

    async function getFileFromEndpoint(endPoint: string) {
        getReport(endPoint)
    }

</script>

{#await report_status}
    <p> Check Status ... </p>
{:then response}
    {#if response == '"Report"'}
        <p transition:fade style="color: green;"> Proccess succed with no errors</p>
        <button on:click={() => getFileFromEndpoint('get-report')}> Download Reports </button>
    {:else if response == '"Error"'}
        <p transition:fade style="color: red;"> Proccess Failed, but generated error report</p>
        <button on:click={() => getFileFromEndpoint('get-error-report')}> Download Errors </button>
    {/if}
{:catch error}
<p style="color: red">{error.message}</p>
{/await}


<style>
 p{
    text-align: center;
 }
</style>