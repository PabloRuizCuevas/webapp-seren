<script lang="ts">
    import Bars from "./bars.svelte"
    import Label from "./Label.svelte"

    let animation = true
    let salary = 10
    let pension = 8
    let sick = 2
    let accident = 2

</script>

<Bars animation={animation} salary={salary} pension={pension} sick={sick} accident={accident} />

<div class='Containers'>

  <Label bind:output={salary} bind:animation={animation} desc={'Salary:'} ></Label>
  <Label bind:output={pension} bind:animation={animation} desc={'Pension:'} ></Label>
  <Label bind:output={sick} bind:animation={animation} desc={'Sick:'} ></Label>
  <Label bind:output={accident} bind:animation={animation} desc={'Accident:'} ></Label>
  
</div>

<style>

  .Containers {
    display: flex;
    flex-wrap: wrap;    
  }
</style>