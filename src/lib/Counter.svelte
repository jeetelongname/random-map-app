<script>
  let count = 0
  const increment = () => {
    count += 1
  }

 let decCount = 0

 const dec = () => {
   decCount += -1
 }
</script>

<button on:click={increment}>
  count is {count}
</button>

<button on:click={dec}>
  count is {decCount}
</button>
