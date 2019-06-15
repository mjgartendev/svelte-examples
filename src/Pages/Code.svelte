<svelte:head>
<title>Svelte Examples | Markdown</title>
</svelte:head>

<div>
  <section>
    <Monaco 
      name="html"
      value={html}
      language="html"
      on:keyup={(e) => html = e.target.value}
    />
  </section>
  <section>
    {@html html}
  </section>
</div>

<script>
  import Monaco from '../Components/Monaco.svelte';
  let html = "<h1>Hello Monaco!</h1>";
  $: console.log(html);
</script>

<style>
    div {
      height: 100%; 
      width: 100%;
      display: grid; 
      grid-template-columns: 1fr 1fr;
    }
    *, *::before, *::after {box-sizing: border-box}
    
</style>