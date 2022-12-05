<svelte:head>
	<title>Dashboard</title>
	<meta name="description" content="About this app" />
</svelte:head>


<script lang="ts">

  import BarsHandler from "./components/barsHandler.svelte"
  import Donut from "./components/donutHandler.svelte"
  import Table from "./components/tableHandler.svelte"

</script>

<main>
  <h1> My Dashboard</h1>

  <div class='container'>
    <div class='item'>
      <BarsHandler/>
    </div>

    <div class='item'>
      <Donut/>
    </div>

    <div class='item'>
      <Table/>
    </div>
  </div>
 
</main>


<style>

  main {
    max-width: 94rem;
    display: flex;
    flex-wrap: wrap;
  }

  .container {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
  }

  .item{
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
  
    border-radius: 10px;
    border-color: black;

    max-width: 40rem;
    
    flex-grow: 4;

    padding: 10px;
    margin: 2px;
    border:0;
    box-shadow:0 0 15px 4px rgba(0,0,0,0.06);
  }

	h1 {
    color: grey;
		/* display: flex; */
		justify-content: space-between;
    align-items: center;
	}

</style>
