<script lang="ts" module>
  export interface SearchDisplayFilters {
    isNotInAlbum?: boolean;
    isArchive?: boolean;
    isFavorite?: boolean;
  }
</script>

<script lang="ts">
  import Checkbox from '$lib/components/elements/checkbox.svelte';
  import { t } from 'svelte-i18n';

  interface Props {
    filters: SearchDisplayFilters;
  }

  let { filters = $bindable() }: Props = $props();
</script>

<div id="display-options-selection">
  <fieldset>
    <legend class="immich-form-label">{$t('display_options').toUpperCase()}</legend>
    <div class="flex flex-wrap gap-x-5 gap-y-2 mt-1">
      <Checkbox id="not-in-album-checkbox" label={$t('not_in_any_album')} bind:checked={filters.isNotInAlbum} />
      <Checkbox id="archive-checkbox" label={$t('archive')} bind:checked={filters.isArchive} />
      <Checkbox id="favorite-checkbox" label={$t('favorites')} bind:checked={filters.isFavorite} />
    </div>
  </fieldset>
</div>
