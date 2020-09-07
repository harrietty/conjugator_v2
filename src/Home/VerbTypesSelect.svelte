<script lang="ts">
  import { verbTypes } from "./Values.svelte";
  export let selected: string;
</script>

<p>What type of verbs to you want to practice?</p>

{#each verbTypes.options as type}
  <label>
    <input type="radio" bind:group={selected} value={type} />
    {type}
  </label>
{/each}
