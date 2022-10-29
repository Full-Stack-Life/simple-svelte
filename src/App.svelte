<script>
  /**
   * Todo arquivo .svelte é um componente que encapsula HTML, Javascript e CSS
   * 
   * 
   **/
  import Counter from './lib/Counter.svelte'
  import Hello from './lib/Hello.svelte'
  import Html from './lib/Html.svelte';
  import Reactivity from './lib/Reactivity.svelte';
  import ConditionalRend from './lib/ConditionalRend.svelte';
  import { count } from './store/store'

  let viewCount

  count.subscribe(value => {
    viewCount = value
  })

  /**
   * É possível passar as props em um objeto e
   * fazer um spread no componente
   */
  const props = {
    prop: 'teste',
    prop1: 'teste1',
    prop2: 'teste2'
  }

</script>

<main>
  <h1>Im store value: {viewCount}</h1>
  <div class="card">
    <Counter />
  </div>
  <hr>
  <div>
    <Hello />
  </div>
  <hr>
  <Html />
  <hr>
  <Reactivity prop="prop" prop1="prop1" prop2="Value" />
  <Reactivity prop="prop" prop1="prop1" />
  <Reactivity  {...props} />
  <hr>
  <ConditionalRend />
</main>
