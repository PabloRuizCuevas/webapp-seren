<svelte:head>
	<title>Upload</title>
	<meta name="description" content="About this app" />
</svelte:head>


<script lang="ts">
    import Dropzone from "svelte-file-dropzone";
    import List from "./List.svelte"
    import Upload from "./Upload.svelte"
    
    interface Files {
        accepted: any,
        rejected: any
    }

    let files: Files = {
      accepted: [],
      rejected: []
    };
  
    function handleFilesSelect(e: any) {
      /* it seems e already has a acecepted and rejected list on it
      console.log(e) */
      const { acceptedFiles, fileRejections } = e.detail;
      files.accepted = [...files.accepted, ...acceptedFiles];
      files.rejected = [...files.rejected, ...fileRejections];
    }

</script>

<main>
  <div class="text-column">
    <h1>Drag & Drop</h1>

      <Dropzone on:drop={handleFilesSelect} accept=".xlsx"/> <!--  probably also csv etc -->
      <Upload files={files}></Upload>
      <List files={files.accepted}/>
  </div>
</main>

<style>

	h1 {
        color: grey;
		/* display: flex; */
		justify-content: space-between;
        align-items: center;
	}

</style>