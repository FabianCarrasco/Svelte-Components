<!--

  LIFECYCLE HOOKS

  onMount hook: The onMount function schedules the passed in callback
    to run as soon as the component has been mounted on the DOM

    If you return a function from the callback function, that function
    will be called when the component is unmounted

    It is in this hook that you'd make HTTP requests, perform DOM 
    manipulations and setup timers or event listeners.
  
  onDestroy hook: This hook schedules a callback to run immediately before
    the component is unmounted

    You could perform tasks like clearing timers and removing event listeners

    onMount does not render inside a server-side component whereas onDestroy does

  beforeUpdate hook: The beforeUpdate hook schedules a callback to run immediately
    before the component is updated
  
  afterUpdate hook: The afterUpdate hook schedules a callback to run immediately
    after the component has been updated

  The beforeUpdate & afterUpdate hook can be used to access the existing DOM before
    and after an update

  tick hook: The tick function returns a promise that resolves once any pending
    state changes have been applied

    The tick function is unlike other lifecycle functions in that you can call it
    any time and not just when the component first initializes

    It does help when you want to run some code after pending changes have been
    applied to the DOM

  SPECIAL ELEMENTS

  svelte:component - For dynamic components

  svelte:self - Allows a component to contain itself recursively

  svelte:window - Add event listeners to the window object

  svelte:body - Listen for events that fire on the document body

  svelte:head - Insert elements inside the <head> of your document

  svelte:options - Specify compiler options
 -->
<script lang="ts">
  import PostList from "./lib/components/PostList.svelte";
  import AutoFocus from "./lib/components/AutoFocus.svelte";
  import TabA from "./lib/components/TabA.svelte";
  import TabB from "./lib/components/TabB.svelte";
  import TabC from "./lib/components/TabC.svelte";
  import Counter, {getTotalCount} from "./lib/components/Counter.svelte";
  let activeTab = TabA 
</script>

<main>
  <button on:click={() => alert(getTotalCount())}>Alert total count</button>
  <Counter/>
  <Counter/>
  <Counter/>
  <button on:click={() => (activeTab = TabA)}>Tab A</button>
  <button on:click={() => (activeTab = TabB)}>Tab B</button>
  <button on:click={() => (activeTab = TabC)}>Tab C</button>
  <!-- {#if activeTab === 'TabA'}
    <TabA/>
  {/if}
  {#if activeTab === 'TabB'}
    <TabB/>
  {/if}
  {#if activeTab === 'TabC'}
    <TabC/>
  {/if} -->
  <svelte:component this={activeTab}/>
  <AutoFocus/> 
  <PostList />  
</main>

<style>
</style>