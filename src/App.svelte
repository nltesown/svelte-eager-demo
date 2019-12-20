<script>
  let y;
  import Eager from "./Eager.svelte";
</script>

<style>
  :global(body) {
    margin: 0;
  }
  .main {
    height: 300vh;
  }

  .debug {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 80px;
    height: 30px;
    line-height: 30px;
    background-color: #823439;
    color: #fff;
    text-align: center;
  }

  nav {
    display: block;
    padding: 24px 8px;
    background-color: #323439;
    color: #fff;
    font-size: 2.5rem;
  }
</style>

<svelte:window bind:scrollY={y} />
<div class="debug">{y}</div>

<div class="main">

  <Eager side="top">
    <nav>Hello there! I'm Eager Igor</nav>
  </Eager>

</div>
