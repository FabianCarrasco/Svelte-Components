<script lang="ts">
  import { setContext } from 'svelte'
  import type { children, DispatchOptions } from 'svelte/internal';
  import ComponentC from './components/ComponentC.svelte';
  import Greet from './components/Greet.svelte'
  import Inner from './components/Inner.svelte';
  import Popup from './components/Popup.svelte';
  import Outer from './components/Outer.svelte';
  import Button from './components/Button.svelte';
  import ChildStyles from './components/ChildStyles.svelte';
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


  <h4>App component text</h4>
  <ChildStyles />
  <h3>App component global style</h3>
</main>

<style>
  /*Result is same if applied to child component*/
  :global(h3) {
    color: blue;
  }

  h4 {
    color: orange;
  }


</style>