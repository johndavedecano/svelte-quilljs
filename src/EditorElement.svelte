<svelte:options accessors={true} />

<script>
  import { onMount, createEventDispatcher } from "svelte";

  export let editorRef = {};

  const dispatch = createEventDispatcher();

  onMount(() => dispatch("mounted", editorRef));
</script>

<div bind:this={editorRef} />
