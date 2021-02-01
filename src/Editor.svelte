<svelte:options accessors={true} />

<script>
  import { onMount, onDestroy, createEventDispatcher } from "svelte";
  import EditorElement from "./EditorElement.svelte";

  export let options = {};

  const dispatch = createEventDispatcher();

  let quill;

  export const instance = () => quill;

  const onMounted = ({ detail }) => startQuill(detail);

  const startQuill = (editorRef) => {
    if (editorRef) {
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
    }
  };

  onMount(() => {
    startQuill();
  });

  onDestroy(() => {
    quill = null;
    dispatch("destroyed", quill);
  });
</script>

<EditorElement on:mounted={onMounted} />
