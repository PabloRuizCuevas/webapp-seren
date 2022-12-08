<script lang="ts">
  import Donut from "./donut.svelte"
  import Label from "./Label.svelte"

  let animation = true
  let pension = 0.2
  let tax = 0.45
  let eftax: number
</script>


<div class='Containers'>
  <Donut bind:eftax={eftax} animation={animation} pension={pension} tax={tax}/>
  <Label bind:output={tax} bind:animation={animation} desc={'Income Tax bracket %:'} max={1}></Label>
  <Label bind:output={pension} bind:animation={animation} desc={'Pension % (From gross income):'} max={1}></Label>
  
  <p>Effective Income tax: <b>{Math.round(eftax*100)/100}</b> (Considering pension as tax free)</p>
</div>

<style>
  .Containers {
    display: flex;
    flex-wrap: wrap;    
  }

  p {
    margin: 10px;
    text-align: center;
    padding:10px;
    margin: 5px;
    border:0;
    box-shadow:0 0 15px 4px rgba(0,0,0,0.06);
    border-radius: 10px;
    flex-grow: 4;
  }

	b {
		font-weight: bold;
    color: red
	}

</style>