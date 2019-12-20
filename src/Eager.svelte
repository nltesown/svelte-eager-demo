<script>
  import { onMount } from "svelte";
  // export let side = "top";
  let elem;
  let h;
  let y;
  let lastY;
  let navY;
  let state = "initial";

  onMount(() => {
    h = elem.offsetHeight;
    elem.style.position = "fixed";
    elem.style.top = 0;
    elem.style.width = "100%";
    transitionTo(state);
  });

  const states = {
    initial: function(amount, enter) {
      navY = Math.max(-y, -h);
      elem.style.top = `${navY}px`;
      if (navY === -h) transitionTo("hidden");
    },
    hidden: function(amount, enter) {
      if (amount < 0) transitionTo("moving");
    },
    moving: function(amount, enter) {
      if (enter === true) {
        navY = parseInt(elem.style.top);
      }
      if (amount < 0) {
        navY = Math.min(navY - amount, 0);
        elem.style.top = `${navY}px`;
        if (navY === 0) transitionTo("sticky");
      } else if (amount > 0) {
        navY = Math.max(navY - amount, -h);
        elem.style.top = `${navY}px`;
        if (navY === -h) transitionTo("hidden");
      }
    },
    sticky: function(amount, enter) {
      if (amount > 0) transitionTo("moving");
    }
  };

  function fsm(amount) {
    states[state].call(this, amount, false);
  }

  function transitionTo(_state) {
    state = _state;
    states[state].call(this, 0, true);
  }

  $: {
    if (typeof elem !== "undefined") fsm(y - lastY);
    lastY = y;
  }
</script>

<style>

</style>

<svelte:window bind:scrollY={y} />

<div bind:this={elem}>
  <slot />
</div>
