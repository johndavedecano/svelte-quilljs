<svelte:options accessors={true} />

<script>
  import { onMount, onDestroy, createEventDispatcher } from "svelte";

  export let options = {};

  const dispatch = createEventDispatcher();

  let editorRef;

  let quill;

  export const instance = () => quill;

  const startQuill = () => {
    quill = new window.Quill(editorRef, {
      modules: {
        toolbar: [
          [{ header: [1, 2, 3, false] }],
          ["bold", "italic", "underline", "strike"],
          ["link", "code-block"],
        ],
      },
      placeholder: "Type something...",
      theme: "snow", // or 'bubble'
      ...options,
    });

    dispatch("created", quill);
  };

  onMount(() => {
    startQuill();
  });

  onDestroy(() => {
    quill = null;
    dispatch("destroyed", quill);
  });
</script>

<div bind:this={editorRef} />
