<script lang="ts">
  import { pronouns } from "./Values.svelte";
  export let selected: string[];

  const togglePronoun = (
    e: Event & { target: EventTarget & HTMLInputElement }
  ) => {
    if (e.target.checked) {
      selected = [...selected, e.target.value];
    } else {
      selected = selected.filter((val) => val !== e.target.value);
    }
  };
</script>

<p>What pronouns do you want to practice?</p>

{#each pronouns.options as pronoun}
  <label>
    <input
      value={pronoun}
      type="checkbox"
      checked={selected.includes(pronoun)}
      on:change={togglePronoun} />
    {pronoun}
  </label>
{/each}
