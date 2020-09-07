<script lang="ts">
  import { tenses } from "./Values.svelte";
  export let selected: string[];

  const toggleTense = (
    e: Event & { target: EventTarget & HTMLInputElement }
  ) => {
    if (e.target.checked) {
      selected = [...selected, e.target.value];
    } else {
      selected = selected.filter((val) => val !== e.target.value);
    }
  };
</script>

<p>What tenses do you want to practice?</p>
{#each tenses.options as tense}
  <label>
    <input
      value={tense}
      type="checkbox"
      checked={selected.includes(tense)}
      on:change={toggleTense} />
    {tense}
  </label>
{/each}
