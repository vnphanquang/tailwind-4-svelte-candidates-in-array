# Reproduction - TailwindCSS 4 + Svelte - Candidates in JS array

Reproduction for https://github.com/tailwindlabs/tailwindcss/issues/15148

Steps:

1. Clone this repository
2. Install dependencies: `pnpm install`
3. Run build and preview: `pnpm build && pnpm preview`

Expected result: preview site should display 4 boxes with colors: red, green, blue, tomato, respectively.

Actual result: preview site displays nothing

Affected code:

- [src/App.svelte](src/App.svelte)
- [src/app.css](src/app.css)

## Discussion

It seems that tailwind will miss candidates inside a JS array with length > 3. Code of interest:

```svelte
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
```

Delete or comment out any of the classes in the array and it will work:

```svelte
<script>
  const classes = [
    'test-red',
    'test-green',
    'test-blue',
    // 'test-tomato', 
  ];
</script>

{#each classes as cls}
    <div class="{cls}"></div>
{/each}
```

Interestingly, adding an inline comment makes it work too:

```svelte
<script>
  const classes = [
    'test-red',
    'test-green',
    'test-blue',
    'test-tomato', // some comment
  ];
</script>

{#each classes as cls}
    <div class="{cls}"></div>
{/each}
```
