
<script lang="ts">
    import { fade } from 'svelte/transition';
    export let promise: any = null


    interface Files {
        accepted: any,
        rejected: any
    }

    export let files: Files

    async function sendFiles(){
        promise = true
        if (files.accepted.length === 0){
            console.log('nothing here')
        }
        console.log('aqui')
        
        my_promise = Promise.all(files.accepted.map(async (file: any) => {
            await uploadFile(file);
        }));
        
    }

    let my_promise : Promise<any> | null  = null


    async function getReport() {
        console.log('reports')
        const formData = new FormData();
        formData.append('name', 'file.name');
        const download = fetch('http://127.0.0.1:8000/get-report', {
            method: 'POST'
        })
        .then(response => response.blob())
        .then(blob => {
            var url = window.URL.createObjectURL(blob);
            var a = document.createElement('a');
            a.href = url;
            a.download = "Report.xlsx";
            document.body.appendChild(a); // we need to append the element to the dom -> otherwise it will not work in firefox
            a.click();    
            a.remove();  //afterwards we remove the element again         
        });
        }


    async function uploadFile(file: any){
        const formData = new FormData();
        formData.append('name', 'file.name');
        formData.append('file', file);
        const upload = fetch('http://127.0.0.1:8000/upload-file', {
            method: 'POST',
            body: formData,
            mode: 'no-cors'
        })
        
        return upload
    }

    async function test(file: any){
        const upload = fetch('http://127.0.0.1:8000/test', {
            method: 'GET'
        })
        console.log('request ')
        return upload
    }
      
</script>

<button on:click={sendFiles}> Submmit Files </button>

{#if promise != null }
    {#await my_promise}
        <p transition:fade>...waiting</p>
    {:then response}
        <p>Files succesfully uploaded</p>
    {:catch error}
        <p style="color: red">{error.message}</p>
    {/await}
{/if}

<button on:click={getReport}> Download Reports </button>


<style>
    

</style>