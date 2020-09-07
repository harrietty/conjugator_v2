<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import { language } from "./Values.svelte";
  const languages = language.options;

  const dispatch = createEventDispatcher();

  export let selected: string;

  function dispatchChange(e) {
    dispatch("change", e);
  }
</script>

<label for="language">What language are you learning? <select
    id="language"
    on:blur={dispatchChange}
    bind:value={selected}>
    {#each languages as language}
      <option value={language}>{language}</option>
    {/each}
    <option value={'comingSoon'} disabled>More languages coming soon!</option>
  </select>
</label>
