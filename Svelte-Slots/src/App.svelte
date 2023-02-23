<script lang="ts">
  import Card from "./components/Card.svelte";
  import CardA from "./components/CardA.svelte";
  import NameList from "./components/NameList.svelte";
</script>

<main>
  <NameList>
    <h3 slot='hero' let:firstName let:lastName>
      {firstName} {lastName}
    </h3>
  </NameList>
  
  <NameList>
    <h3 slot="hero" let:firstName let:lastName>
      {lastName}, {firstName}
    </h3>
  </NameList>
  
  <NameList>
    <h3 slot="hero" let:firstName>
      {firstName}
    </h3>
  </NameList>
  
  <Card>Card content</Card>  
  <Card><h2>Card Content</h2></Card>
  <Card><img src="https://picsum.photos/200" alt=""></Card>
  <Card/>
  <CardA>
    <div slot="header">
      <h3>Header</h3>
    </div>
    <div slot="content">
      <img src="https://picsum.photos/200" alt="">
    </div>
    <div slot="footer">
      <button>View Details</button>
    </div>
  </CardA>
  <CardA>
    <div slot="header">
      <h3>Header</h3>
    </div>
    <div slot="content">
      <img src="https://picsum.photos/200" alt="">
    </div>
  </CardA>
</main>

<style>
  
</style>