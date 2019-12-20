<script>
  let y;
  import Eager from "./Eager.svelte";
</script>

<style>
  :global(body) {
    padding: 0;
  }
  .main {
    height: 200vh;
  }

  .debug {
    position: fixed;
    bottom: 0;
    left: 0;
  }

  nav {
    display: block;
    padding: 24px 8px;
    background-color: #323439;
    color: #fff;
    font-size: 2.5rem;
  }
</style>

<!--
  <svelte:window bind:scrollY={y} />
  <div class="debug">{y}</div>
-->

<div class="main">

  <Eager side="top">
    <nav>Hello there! I'm Eager Igor</nav>
  </Eager>

</div>
