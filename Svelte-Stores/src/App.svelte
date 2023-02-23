<!-- 
  Svelte Store - Counter Example
  Counter

  1. Increment
  2. Decrement
  3. Reset
  4. Display
-->


<script lang="ts">
  import Decrement from "./components/Decrement.svelte";
  import Display from "./components/Display.svelte";
  import Increment from "./components/Increment.svelte";
  import Reset from "./components/Reset.svelte";
  import Timer from "./components/Timer.svelte";
</script>

<main>
  <Increment/>
  <Decrement/>
  <Reset/> 
  <Display/>
  <Timer/>
</main>

<style>
</style>