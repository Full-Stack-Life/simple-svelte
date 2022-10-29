<script>
  let user = { loggedIn: false };
  let x = 1;

  function toggle() {
    user.loggedIn = !user.loggedIn;
  }

  const increment = () => x += 1;

  let services = [
    { id: '123asdcdaskajh1a', name: 'service1', cluster: 'cluster1' },
    { id: '1123asdcdaskajhs', name: 'service2', cluster: 'cluster2' },
    { id: '123asdcdaskajh1d', name: 'service3', cluster: 'cluster3' },
    { id: '1123asdcdaskajhg', name: 'service4', cluster: 'cluster4' },
    { id: '123asdcdaskajh1h', name: 'service5', cluster: 'cluster5' }
  ];

  const removeService = () => services = services.slice(1);
</script>

<!-- 
  # -> inicio
  : -> continuação
  / -> fim
 -->

{#if user.loggedIn}
  <button on:click={toggle}> Log out </button>
{/if}

{#if !user.loggedIn}
  <button on:click={toggle}> Log in </button>
{/if}

<!-- OU -->

{#if user.loggedIn}
  <button on:click={toggle}> Log out </button>
{:else}
  <button on:click={toggle}> Log in </button>
{/if}

{#if x > 10}
  <p>{x} is greater than 10</p>
{:else if 5 > x}
  <p>{x} is less than 5</p>
{:else}
  <p>{x} is between 5 and 10</p>
{/if}

<button on:click={increment}>Increment X</button>

<!-- Se eu não passar o id o Svelte não sabe qual nó exatamente mudar
ele sempre irá adicionar e remover no final do bloco e atualiza
todos os valores alterados.
Ou seja, se tento remover o primeiro elemento o Svelte atualiza todos e remove o último.

Para que isso não aconteça e apenas um elemento seja modificado basta passar um id
no each. -->
<table>
  <tr>
    <th>Service</th>
    <th>Cluster</th>
  </tr>
  {#each services as service (service.id)}
    <tr>
      <td>{service.name}</td>
      <td>{service.cluster}</td>
    </tr>
  {/each}
</table>

<!-- OU -->

<table>
  <tr>
    <th>Indice</th>
    <th>Service</th>
    <th>Cluster</th>
  </tr>
  {#each services as { id, name, cluster }, i (id)}
    <tr>
      <td>{i}</td>
      <td>{name}</td>
      <td>{cluster}</td>
    </tr>
  {/each}
</table>

<button on:click={removeService}>Remove services</button>

<style>
table {
  margin-top: 50px;
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}

button {
  margin: 20px;
}
</style>
