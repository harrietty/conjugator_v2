<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import LanguageSelect from "./LanguageSelect.svelte";

  const dispatch = createEventDispatcher();

  export let selected: string;

  function dispatchChangeLanguage(event) {
    dispatch("changeLanguage", event.detail);
  }
</script>

<form>
  <LanguageSelect bind:selected on:change={dispatchChangeLanguage} />
</form>
