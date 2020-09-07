<script lang="ts">
  import QuickStartForm from "./Home/QuickStart.svelte";
  import AdvancedForm from "./Home/Advanced.svelte";
  import { language, tenses, pronouns, verbTypes } from "./Home/Values.svelte";

  let quickStart: boolean = true;
  let selectedLanguage: string = language.default;
  let selectedTenses: string[] = tenses.default;
  let selectedPronouns: string[] = pronouns.default;
  let selectedVerbType: string = verbTypes.default;
  let selectedVerbs: string[] = [];

  let verbOptions = [];

  async function fetchVerbs(e) {
    console.log(e, "time to fetch new verbs");
  }
</script>

<style>
  .moreOptions {
    color: blue;
    font-size: 12px;
    cursor: pointer;
  }
</style>

<h1>Conju-Gator</h1>
<p>Conjugate all the verbs!</p>

{#if quickStart}
  <QuickStartForm
    bind:selected={selectedLanguage}
    on:changeLanguage={fetchVerbs} />
  <button> Let's go! </button>
  <p class="moreOptions" on:click={() => (quickStart = false)}>
    Show me more options
  </p>
{:else}
  <AdvancedForm
    on:changeLanguage={fetchVerbs}
    bind:selectedLanguage
    bind:selectedTenses
    bind:selectedPronouns
    bind:selectedVerbType
    bind:selectedVerbs />
{/if}

<pre>
	{selectedLanguage}
	{selectedTenses}
	{selectedPronouns}
  {selectedVerbType}
  {JSON.stringify(selectedVerbs)}
</pre>
