<script>
  export let code = "";

  import copy from "clipboard-copy";
  import { CodeSnippet } from "carbon-components-svelte";
</script>

<CodeSnippet
  {...$$restProps}
  code="{code}"
  on:click="{() => {
    copy(code);
  }}"
/>
