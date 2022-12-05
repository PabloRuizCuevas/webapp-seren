<script lang="ts">
    import Bars from "./bars.svelte"

    let animation = true
    let salary = 10
    let pension = 8
    let sick = 2
    let accident = 2
</script>

<Bars animation={animation} salary={salary} pension={pension} sick={sick} accident={accident} />

<div class='Containers'>
 
  <label>
    <p>Salary:</p>
    <input type=number on:input="{() => animation=true}" bind:value={salary} min=0 max=10 step=1>
    <input type=range on:input="{() => animation=false}" bind:value={salary}  min=0 max=10 step=0.01>
  </label>

  <label>
    <p>Pension:</p>
    <input type=number on:input="{() => animation=true}" bind:value={pension} min=0 max=10 step=1>
    <input type=range on:input="{() => animation=false}" bind:value={pension} min=0 max=10 step=0.01>
  </label>

  <label>
    <p>Sick:</p>
    <input type=number on:input="{() => animation=true}" bind:value={sick} min=0 max=10 step=1>
    <input type=range on:input="{() => animation=false}" bind:value={sick} min=0 max=10 step=0.01>
  </label>

  <label>
    <p>Accident:</p>
    <input type=number on:input="{() => animation=true}" bind:value={accident} min=0 max=10 step=1>
    <input type=range on:input="{() => animation=false}" bind:value={accident} min=0 max=10 step=0.01>
  </label>

</div>

<style>

  .Containers {
    display: flex;
    flex-wrap: wrap;

    
  }

  p {
    margin: 10px;
    text-align: center;
  }

  label {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
  
    border-radius: 10px;
    border-color: black;
    
    flex-grow: 4;

    padding:10px;
    margin: 5px;
    border:0;
    box-shadow:0 0 15px 4px rgba(0,0,0,0.06);
  }

  input {
    align-items: center;
  }

  input {
    text-align: center;  
    border: 1px solid #6C757D;
  } 

  input[type="number"] {
    -webkit-appearance: textfield !important;
    -moz-appearance: textfield !important;
    appearance: textfield !important;
    }

  input[type=number]::-webkit-inner-spin-button,
  input[type=number]::-webkit-outer-spin-button {
      -webkit-appearance: none;
    }
</style>