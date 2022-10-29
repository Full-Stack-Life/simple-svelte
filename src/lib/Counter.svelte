<script>
  import { count } from '../store/store';

  let viewCount = 0

  count.subscribe(value => {
    viewCount = value
  })

  const increment = () => {
    count.update(value => value + 1)
  }

</script>

<!-- Esse evento atualiza diretamento o DOM -->
<button on:click={increment}>
  My count is {viewCount}
</button>
