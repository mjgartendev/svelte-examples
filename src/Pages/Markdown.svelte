<svelte:head>
<title>Svelte Examples | Markdown</title>
</svelte:head>

<div>
  <section>
  <Monaco 
    language="markdown"
    value={value}
    name="markdown"
    on:keyup={(e) => value = e.target.value}
  />
</section>
  <section>
    {@html marked(value)}
  </section>
</div>

<script>
  import Monaco from '../Components/Monaco.svelte'
  import marked from 'marked'
  let value = "# Hello marked";
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