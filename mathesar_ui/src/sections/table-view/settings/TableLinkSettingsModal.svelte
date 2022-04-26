<script lang="ts">
  import { faCheck } from '@fortawesome/free-solid-svg-icons';
  import type { ModalController } from '@mathesar-component-library';
  import {
    CancelOrProceedButtonPair,
    ControlledModal,
  } from '@mathesar-component-library';
  import type { TableEntry } from '@mathesar/AppTypes';
  import Identifier from '@mathesar/components/Identifier.svelte';
  import { toast } from '@mathesar/stores/toast';
  import TableLinkSettings from './TableLinkSettings.svelte';

  export let controller: ModalController;
  export let table: TableEntry;

  function handleSave() {
    toast.error('Implementation will be finished in #955');
    return Promise.resolve(undefined);
  }
</script>

<ControlledModal {controller}>
  <div slot="title">
    Table Link Settings for <Identifier>{table.name}</Identifier>
  </div>

  <TableLinkSettings {table} />

  <CancelOrProceedButtonPair
    slot="footer"
    onProceed={handleSave}
    onCancel={() => controller.close()}
    proceedButton={{ label: 'Save', icon: { data: faCheck } }}
  />
</ControlledModal>
