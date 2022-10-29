<script>
  import { count } from '../store/store';

  let viewCount

  count.subscribe(value => {
    viewCount = value
  })

  const increment = () => {
    count.update(value => value + 1)
  }

</script>

<button on:click={increment}>
  My count is {viewCount}
</button>
