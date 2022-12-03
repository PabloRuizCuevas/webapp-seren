<svelte:head>
	<title>Dashboard</title>
	<meta name="description" content="About this app" />
</svelte:head>


<script lang="ts">


  import Bars from "./bars.svelte"
  import Line from "./line.svelte"
  import BarsHandler from "./barsHandler.svelte"
  import Table from "./table.svelte"

  var tableData = [
    {id:1, name:"Billy Bob", age:"12", gender:"male", height:1, col:"red", dob:"", cheese:1},
    {id:2, name:"Mary May", age:"1", gender:"female", height:2, col:"blue", dob:"14/05/1982", cheese:true},
]

</script>

<h1> My Dashboard</h1>

<!-- <Table/> -->

<BarsHandler/>
<Line/>



<style>

	h1 {
        color: grey;
		/* display: flex; */
		justify-content: space-between;
        align-items: center;
	}

</style>
