<script lang="ts">
  import Table from "./table.svelte"

  const columns = [
    { title: "Social Security N", field: "ssn", width: 180 },
    { title: "Name", field: "name", width: 80 },
    { title: "Age", field: "age", hozAlign: "left" },
    { title: "Gross Income", field: "income" },
    { title: "Pension Supplier", field: "supplier" , width: 180}
  ];

  const data = [
    {id:1, ssn: "05234089" , name:"Henrik", age:32, income:3e6, supplier:"Danica"},
  ];

</script>

<Table data={data} columns={columns}/>


