<script>
  /**
   * Recebendo props de um elemento pai
   */
  export let prop, prop1, prop2 = 'Default value';

  let count = 0
  let count2 = 10
  let doubled = count
  let numbers = [1, 2, 3, 4]

  const increment = () => count += 1
  const increment2 = () => count2 += 1

  const addNumber = () => {
    /**
     * Apenas fazer um push não aciona a reatividade, é
     * necessário fazer uma atribuição
     */
    // numbers.push(numbers.length + 1)
    numbers = [...numbers, numbers.length + 1]
  }

  $: sum = numbers.reduce((t, n) => t + n, 0)
  /**
   * A reatividade é acionada com base em atribuições
   * 
   * Regra Básica: a variável reativa deve sempre ser atribuida a ela mesma de alguma
   * forma para a reatividade aconteça
   * 
   * Com o Svelte é possível sincronizar não apenas as váriaveis com o
   * App (DOM), mas também podem reagir a mudanças de estados entre sí,
   * a esse tipo de variavel damos o nome de atributo dinâmico
   * 
   * É possível fazer várias declarações reativas, basta passar $: e declarar
   * a ação, qualquer mudança de estado em uma variável declarada dentro desse
   * bloco irá acionar as ações dentro da declaração
   */
  $: {
    doubled = count * 2
    console.log('reagindo')
  }

  $: console.log('the count is ' + count)

  $: if (count >= 10) {
    alert('count >= 10')
  }

  $: console.log('the count2 is ' + count2)
</script>

<p>
  The double of {count} id {doubled}
</p>
<button on:click={increment}>
  Count: {count}
</button>

<p>
  Count2 {count2}
</p>
<button on:click={increment2}>
  Count: {count2}
</button>

<hr>

<p>{numbers.join(' + ')} = {sum}</p>
<button on:click={addNumber}>Add Number</button>

<hr>

<h1>Prop: {prop}</h1>
<h1>Prop1: {prop1}</h1>
<h1>Prop2: {prop2}</h1>
