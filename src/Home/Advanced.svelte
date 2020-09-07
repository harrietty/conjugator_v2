<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import LanguageSelect from "./LanguageSelect.svelte";
  import TensesSelect from "./TensesSelect.svelte";
  import PronounsSelect from "./PronounsSelect.svelte";
  import VerbTypesSelect from "./VerbTypesSelect.svelte";
  import VerbsSelect from "./VerbsSelect.svelte";

  export let selectedLanguage: string;
  export let selectedTenses: string[];
  export let selectedPronouns: string[];
  export let selectedVerbType: string;
  export let selectedVerbs: string[];
  export let options;

  const dispatch = createEventDispatcher();

  function dispatchChangeLanguage(event) {
    dispatch("changeLanguage", event.detail);
  }
</script>

<form>
  <LanguageSelect
    bind:selected={selectedLanguage}
    on:change={dispatchChangeLanguage} />
  <TensesSelect bind:selected={selectedTenses} />
  <PronounsSelect bind:selected={selectedPronouns} />
  <VerbTypesSelect bind:selected={selectedVerbType} />
  {#if selectedVerbType === 'Specific'}
    <VerbsSelect bind:selected={selectedVerbs} {options} />
  {/if}
</form>
