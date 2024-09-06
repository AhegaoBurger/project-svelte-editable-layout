<script lang="ts">
	import { onMount, createEventDispatcher } from 'svelte';
	import { browser } from '$app/environment';
	import { createSwapy } from 'swapy';
	import EditSwitch from './edit-switch.svelte';

	type SectionKey = 'top' | 'center_left' | 'center_right' | 'bottom';

	const DEFAULT = {
		'1': 'top' as SectionKey,
		'2': 'center_left' as SectionKey,
		'3': 'center_right' as SectionKey,
		'4': 'bottom' as SectionKey
	};

	export let sectionSlotClassNames: {
		[key in keyof typeof DEFAULT]: string;
	};
	export let defaultEditing: boolean;

	let isEditing = defaultEditing;
	let containerElement: HTMLElement;

	const dispatch = createEventDispatcher();

	$: slotItems = browser
		? JSON.parse(localStorage.getItem('dashSlotItems') || JSON.stringify(DEFAULT))
		: DEFAULT;

	onMount(() => {
		if (browser && containerElement) {
			const swapy = createSwapy(containerElement);
			swapy.onSwap(({ data }) => {
				localStorage.setItem('dashSlotItems', JSON.stringify(data.object));
				dispatch('swap', data.object);
			});
		}
	});

	function getClassName(slotId: string): string {
		return sectionSlotClassNames[slotId as keyof typeof sectionSlotClassNames] || '';
	}
</script>

<EditSwitch bind:checked={isEditing} {defaultEditing} />

<div bind:this={containerElement} id="swap-layout" {...$$restProps}>
	{#each Object.entries(slotItems) as [slotId, sectionKey]}
		<div data-swapy-slot={slotId} class={getClassName(slotId)}>
			<div data-swapy-item={sectionKey} class="relative h-full">
				{#if isEditing}
					<span
						data-swapy-handle
						class="absolute left-0 top-0 z-10 box-border flex flex-grow cursor-move items-center rounded-sm bg-slate-200 p-1"
					>
						<svg y="0px" viewBox="0 0 511.987 511.987" width="16" height="16">
							<path
								d="M507.595,245.391l-66.97-66.97c-5.857-5.858-15.355-5.858-21.213,0c-5.858,5.858-5.858,15.355,0,21.213L460.778,241H270.991  V51.214l41.366,41.366c5.857,5.858,15.356,5.858,21.213,0c5.858-5.858,5.858-15.355,0-21.213L266.598,4.394  c-5.857-5.858-15.355-5.858-21.213,0l-66.973,66.973c-5.858,5.858-5.858,15.355,0,21.213c5.857,5.858,15.355,5.858,21.213,0  l41.366-41.366V241H51.204l41.366-41.366c5.858-5.858,5.858-15.355,0-21.213c-5.857-5.858-15.355-5.858-21.213,0l-66.97,66.97  c-0.351,0.35-0.682,0.719-0.997,1.103c-4.901,5.963-4.405,14.716,0.997,20.115l66.97,66.97c5.857,5.858,15.356,5.858,21.213,0  c5.858-5.858,5.858-15.355,0-21.213L51.204,271h189.787v189.787l-41.366-41.366c-5.857-5.858-15.355-5.858-21.213,0  c-5.858,5.858-5.858,15.355,0,21.213l66.97,66.97c5.757,5.761,15.296,5.926,21.218,0l66.97-66.97c5.858-5.858,5.858-15.355,0-21.213  c-5.857-5.858-15.355-5.858-21.213,0l-41.366,41.366V271h189.787l-41.366,41.366c-5.858,5.858-5.858,15.355,0,21.213  c5.857,5.858,15.356,5.858,21.213,0l66.97-66.97C513.375,260.834,513.514,251.306,507.595,245.391z"
							></path>
						</svg>
					</span>
				{/if}
				{#if sectionKey === 'top'}
					<slot name="top" />
				{:else if sectionKey === 'center_left'}
					<slot name="center_left" />
				{:else if sectionKey === 'center_right'}
					<slot name="center_right" />
				{:else if sectionKey === 'bottom'}
					<slot name="bottom" />
				{/if}
			</div>
		</div>
	{/each}
</div>
