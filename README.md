# Quill for SvelteJS

Your powerful rich text editor for your sveltejs applications.

## How to install
```
npm install svelte-quilljs
```
Then add quilljs assets on your public/index.html
```
<head>
	<meta charset='utf-8'>
	<meta name='viewport' content='width=device-width,initial-scale=1'>

	<title>Svelte app</title>

	<link rel='icon' type='image/png' href='/favicon.png'>
	<link rel='stylesheet' href='/global.css'>
	<link rel='stylesheet' href='/build/bundle.css'>
	<link
    href="https://cdn.quilljs.com/1.3.7/quill.snow.css"
    rel="stylesheet"
  /><script
    src="https://cdn.quilljs.com/1.3.6/quill.js"></script>
	<script defer src='/build/bundle.js'></script>
</head>
```

Then on your App.svelte you use it like the following:
```
<script>
  import { onMount } from "svelte";

  import Editor from "svelte-quilljs";

  let editor;

  onMount(() => {
    console.log(editor.instance());
  });
</script>

<Editor bind:this={editor} />

```

### Accessing quill instance
```
editor.instance()
```

**Setting Contents** - https://quilljs.com/docs/api/#content

**Handling Events** - https://quilljs.com/docs/api/#events

Please read quilljs documentation for more informations.