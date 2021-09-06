<script>
  import { personData } from './data/person-data.js';
  // console.log(personData);

  const tableHeaders = Object.keys(personData[0]);

  let sortedPersonData = personData;

  let selected = 'id';
  
	let ascendingOrder = true;

  const sortByNumber = (tableHeader) => {
    sortedPersonData = sortedPersonData.sort((obj1, obj2) => {
      return ascendingOrder ? Number(obj1[tableHeader]) - Number(obj2[tableHeader])
			: Number(obj2[tableHeader]) - Number(obj1[tableHeader]);
    });

    selected = tableHeader;
  }

  const sortByString = (tableHeader) => {
    sortedPersonData = sortedPersonData.sort((obj1, obj2) => {
      if (obj1[tableHeader] < obj2[tableHeader]) {
        return -1;
      }
      else if (obj1[tableHeader] > obj2[tableHeader]) {
        return 1;
      }

      return 0;
    });

    if (!ascendingOrder) {
			sortedPersonData = sortedPersonData.reverse()
		}

    selected = tableHeader;
  }
</script>

<!-- MarkUp -->
<section id="sorting">
<h2>Sort Table</h2>
<table id="myTable">
    <tr>
      {#each tableHeaders as header}
        <th class:highlight={selected === header}
          on:click={() => (header === "id" || header === "age" ? sortByNumber(header) : sortByString(header))}>
            {header.replace("_", " ")}

            {#if header === selected}	
              <span class="order-icon" on:click={() => ascendingOrder = !ascendingOrder}>
                {@html ascendingOrder ? "&#10515;" : "&#10514;"}
              </span>		
            {/if}	
        </th>
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
</section>

<style>
table {
  border-spacing: 0;
  width: 100%;
  border: 1px solid #ddd;
}

th {
  text-transform: uppercase;
  font-weight: bold;
  cursor: pointer;
}

.highlight {
  color: crimson;
}

th, td {
  text-align: left;
  padding: 16px;
}

tr:nth-child(even) {
  background-color: #f2f2f2
}
</style>