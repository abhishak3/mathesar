<script lang="ts">
  import { getContext } from 'svelte';
  import { faCheck } from '@fortawesome/free-solid-svg-icons';
  import type { ModalController } from '@mathesar-component-library';
  import {
    CancelOrProceedButtonPair,
    ControlledModal,
  } from '@mathesar-component-library';
  import Identifier from '@mathesar/components/Identifier.svelte';
  import type { TabularDataStore } from '@mathesar/stores/table-data/types';
  import { tables } from '@mathesar/stores/tables';
  import { toast } from '@mathesar/stores/toast';
  import TableLinkSettings from './TableLinkSettings.svelte';

  const tabularData = getContext<TabularDataStore>('tabularData');

  export let controller: ModalController;

  $: table = (() => {
    const t = $tables.data.get($tabularData.id);
    if (!t) {
      // This should never happen because the user shouldn't be able to open
      // the modal if the table doesn't exist. But we throw an error here to
      // make sure that `table` is always defined.
      throw new Error('Unable to configure a table ling without a base table');
    }
    return t;
  })();

  function init() {
    // TODO
  }

  function handleSave() {
    toast.error('Implementation will be finished in #955');
    return Promise.resolve(undefined);
  }
</script>

<ControlledModal {controller} on:open={init}>
  <div slot="title">
    Settings for Table <Identifier>{table.name}</Identifier>
  </div>

  <TableLinkSettings {table} />

  <CancelOrProceedButtonPair
    slot="footer"
    onProceed={handleSave}
    onCancel={() => controller.close()}
    proceedButton={{ label: 'Save', icon: { data: faCheck } }}
  />
</ControlledModal>
