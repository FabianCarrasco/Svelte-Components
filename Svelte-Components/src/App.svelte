<script lang="ts">
  import { setContext } from 'svelte'
  import type { DispatchOptions } from 'svelte/internal';
  import ComponentC from './components/ComponentC.svelte';
  import Greet from './components/Greet.svelte'
  import Inner from './components/Inner.svelte';
  import Popup from './components/Popup.svelte';
  import Outer from './components/Outer.svelte';
  import Button from './components/Button.svelte';
  const name = 'Fabian'
  const channel = 'OneByteOfRam'
  const obj = {
    name: 'Barry',
    heroName: 'Flash',
  }
  const userName = 'Tacomaker'
  setContext('username-context', userName)

  let showPopup = false

  function closePopup(event: CustomEvent<String>) {
    showPopup = false
    console.log(event.detail)
  }

  function handleGreet(event: CustomEvent<String>) {
    alert(event.detail)
  }
</script>

<main>
  <Greet name='Bruce' heroName='Batman'/>
  <Greet name='Clark' heroName='Superman'/>
  <Greet name='Diana' heroName='Wonder Woman'/>
  <Greet name={name} heroName={channel}/>
  <Greet {name} heroName={channel}/>
  <Greet {name}/>
  <Greet name={obj.name} heroName={obj.heroName}/>
  <Greet {...obj}/>
  <ComponentC/>
  
  <button on:click={() => (showPopup = true)}>Show Popup</button>
  {#if showPopup}
    <Popup on:close={() => (showPopup = false)}/>
    <Popup on:close={closePopup}/>
  {/if}
  

  <Outer on:greet={handleGreet}/>

  <Button on:click={() => alert('Clicked')}>Click</Button> 
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>