<script>
  const classes = [
    'test-red',
    'test-green',
    'test-blue',
    'test-tomato', 
  ];
</script>

{#each classes as cls}
    <div class="{cls}"></div>
{/each}

