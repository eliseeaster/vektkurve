<script lang="ts">
  import Compositions from "./Compositions.svelte";
  import { openEHR } from "./OpenehrStore";
  import Chart from "./Chart.svelte";
</script>

<Chart />

<!-- {#if $openEHR}
  // Welcome to OpenEHR! // <Compositions />
  //
{:else}
  // Loading client... //
{/if} -->
