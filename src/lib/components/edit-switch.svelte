<!-- src/lib/components/edit-switch.svelte -->
<script lang="ts">
	import { Label } from '$lib/components/ui/label';
	import { Switch } from '$lib/components/ui/switch';
	import { createEventDispatcher } from 'svelte';

	export let defaultEditing: boolean;
	export let checked = defaultEditing;

	const dispatch = createEventDispatcher<{ checkedChange: boolean }>();

	function handleChange(event: Event) {
		const target = event.target as HTMLInputElement;
		checked = target.checked;
		dispatch('checkedChange', checked);
	}
</script>

<div class="flex items-center space-x-2">
	<Switch bind:checked id="edit-mode" on:change={handleChange} />
	<Label for="edit-mode">Enable Edit Mode</Label>
</div>
