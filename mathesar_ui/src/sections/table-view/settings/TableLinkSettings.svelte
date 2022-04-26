<script lang="ts">
  import { getContext } from 'svelte';
  import type { TableEntry } from '@mathesar/AppTypes';
  import type { Column } from '@mathesar/stores/table-data/columns';
  import type { TabularDataStore } from '@mathesar/stores/table-data/types';
  import SelectColumns from '@mathesar/components/SelectColumns.svelte';

  const tabularData = getContext<TabularDataStore>('tabularData');

  export let table: TableEntry;

  $: ({ columnsDataStore } = $tabularData);
  $: availableColumns = $columnsDataStore.columns;

  let columns: Column[] = [];
</script>

<div>Table Link settings</div>

<SelectColumns {availableColumns} bind:columns />
