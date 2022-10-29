<script>
  /**
   * Todo arquivo .svelte é um componente que encapsula HTML, Javascript e CSS
   * 
   * 
   **/
  import Counter from './lib/Counter.svelte'
  import Hello from './lib/Hello.svelte'
  import Html from './lib/Html.svelte';
  import { count } from './store/store'

  let viewCount

  count.subscribe(value => {
    viewCount = value
  })

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
</main>
