<svelte:head>
	<title>Dashboard</title>
	<meta name="description" content="About this app" />
</svelte:head>


<script lang="ts">

  import Bars from "./bars.svelte"
  import Line from "./line.svelte"

</script>

<h1> My Dashboard </h1>
<Bars/>
<Line/>



<style>

	h1 {
        color: grey;
		/* display: flex; */
		justify-content: space-between;
        align-items: center;
	}

</style>