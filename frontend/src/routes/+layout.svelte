<script>
    import "../app.css";
    import { onMount } from "svelte";
	import { watchUserChange } from "../lib/store";

    onMount(() => {
       watchUserChange();
    });
  </script>
  
  <slot />