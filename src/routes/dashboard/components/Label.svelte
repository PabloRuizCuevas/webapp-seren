<script lang="ts">
  export let animation: boolean = true
  export let output: number = 5
  export let desc: string = 'label'
  export let max: number = 10

</script>

<label>
  <p>{desc}</p>
  <input type=number on:input="{() => animation=true}" bind:value={output} min=0 max={max} step=1>
  <input type=range on:input="{() => animation=false}" bind:value={output}  min=0 max={max} step=0.01>
</label>


<style>

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
