<script>
  import { personData } from './data/person-data.js';
  console.log(personData);

  const tableHeaders = Object.keys(personData[0]);

  let sortedPersonData = personData;

  const sortByNumber = (tebleHeader) => {
    sortedPersonData = sortedPersonData.sort((obj1, obj2) => {
      return obj1[tebleHeader] - obj2[tebleHeader];
    });
  }
</script>

<!-- MarkUp -->
<table id="myTable">
    <tr>
      {#each tableHeaders as header}
        <th on:click={() => sortByNumber(header)}>{header.replace("_", " ")}</th>
      {/each}
    </tr>

    {#each sortedPersonData as person}
      <tr>
        <td>{person.id}</td>
        <td>{person.first_name}</td>
        <td>{person.last_name}</td>
        <td>{person.age}</td>
        <td>{person.job}</td>
        <td>{person.country}</td>
      </tr>
    {/each}

  </table>

<style>
table {
  border-spacing: 0;
  width: 100%;
  border: 1px solid #ddd;
}

th {
  text-transform: uppercase;
  cursor: pointer;
}

th, td {
  text-align: left;
  padding: 16px;
}

tr:nth-child(even) {
  background-color: #f2f2f2
}
</style>