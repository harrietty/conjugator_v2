<script lang="ts">
  import Select from "svelte-select";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let selected;
  export let options;
</script>

<p>Choose specific verbs to study</p>
<Select
  isMulti={true}
  items={options}
  bind:selectedValue={selected}
  placeholder="Search verbs"
  noOptionsMessage="No verbs found"
  isClearable={true}
  isSearchable={true} />
