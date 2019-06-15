<script>
  import {onMount} from 'svelte';

  let cards = [
    {title: "one", list: "todo"},
    {title: "two", list: "todo"},
    {title: "three", list: "doing"},
    {title: "four", list: "doing"},
    {title: "five", list: "done"},
    {title: "six", list: "done"}
  ]
  $: console.log(cards)
  let lists = [];
  $: getLists = () => {
    let unique = new Set();
    cards.map(card => unique.add(card.list));
    lists = [...unique]
  }

  onMount(() => getLists())
</script>

<div class="bg-light flex-center">
  {#each lists as list}
    <section class="flex-column bg-grey round">
      <h3>{list}</h3>
      <ul>
        {#each cards as card}
          {#if card.list == list}
            <li class="fg-dark shadow round flex-row">
              {card.title}
              <input class="bg-light round" placeholder={card.list} on:keydown={(e) => {
                if(e.key == "Enter"){
                  {card.list = e.target.value};
                  e.target.value = "";
                  getLists()
                }
              }}/>
            </li>
          {/if}
        {/each}
      </ul>
      <input class="bg-light round" placeholder="add card" on:keydown={(e) => {
        if(e.key == "Enter"){
          cards = [...cards, {title: e.target.value, list: list}]
          e.target.value = ""
        }
      }}/>
    </section>
  {/each}
</div>

<style>
  div{
    justify-content: flex-start;
    padding: 1rem;
  }
  section {
    margin: .25rem 1rem;
    align-self: flex-start;
    padding: 1rem;
    border: 1px solid var(--color-light);
  }
  h3{
    margin: 0;
  }
  li{
    list-style: none; 
    background: white; 
    padding: .5rem 1rem;
    margin-bottom: .5rem;
    min-width: 200px;
  }
  li input {
    width: 40%;
  }
  input {
    width: 100%;
    padding: .25rem;
    text-align: center;
    border: 1px solid var(--color-light);
  }
  ul{
   padding: 0;
  }
  *, *::before, *::after{
    box-sizing:border-box
  }
</style>