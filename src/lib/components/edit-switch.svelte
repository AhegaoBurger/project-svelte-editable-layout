<script lang="ts">
	import { Label } from '$lib/components/ui/label';
	import { Switch } from '$lib/components/ui/switch';
	import { createEventDispatcher } from 'svelte';

	export let defaultEditing: boolean;

	const dispatch = createEventDispatcher<{ checkedChange: boolean }>();

	function handleChange(event: Event) {
		const target = event.target as HTMLInputElement;
		dispatch('checkedChange', target.checked);
	}
</script>

<div class="flex items-center space-x-2">
	<Switch checked={defaultEditing} id="edit-mode" on:change={handleChange} />
	<Label for="edit-mode">Enable Edit Mode</Label>
</div>
