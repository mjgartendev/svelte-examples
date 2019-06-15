<div on:keyup on:change on:input id={name}></div>

<style>
  div {
    font-family: Monaco;
    height: 100%;
    width: 100%;
    padding: 0;
    margin: 0;
  }
  *, *::before, *::after {box-sizing: border-box}
</style>
<script>
  import {onMount} from 'svelte'
  export let theme = 'vs-dark';
  export let language = 'html';
  export let value = "";
  export let name;
  let editor;
  onMount(() => { 
    editor = monaco.editor.create(document.getElementById(name),{
      value: [value].join('/n'),
      language: language,
      theme: theme,
      dragAndDrop: true,
      fontWeight: '500',
      highlightActiveIndentGuide: true,
      lineNumbersMinChars: 2,
      showFoldingControls: "always",
      tabCompletion: "on",
      automaticLayout: true
    });
  });
</script>