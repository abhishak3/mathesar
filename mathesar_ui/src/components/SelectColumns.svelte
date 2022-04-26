<script lang="ts">
  import type { Column } from '@mathesar/stores/table-data/columns';
  import { MultiSelect } from '@mathesar-component-library';
  import type { ComponentAndProps } from '@mathesar-component-library/types';
  import ColumnName from './ColumnName.svelte';

  export let availableColumns: Column[];
  export let columns: Column[] = [];

  function getLabel(column: Column): ComponentAndProps {
    return {
      component: ColumnName,
      props: { column },
    };
  }
</script>

<MultiSelect options={availableColumns} bind:values={columns} {getLabel} />
