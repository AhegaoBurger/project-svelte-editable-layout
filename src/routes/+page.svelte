<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import { UserNav } from '$lib/components/user-nav';
	import { MainNav } from '$lib/components/main-nav';
	import CalendarDateRangePicker from '$lib/components/date-range-picker.svelte';
	import Search from '$lib/components/search.svelte';
	import TeamSwitcher from '$lib/components/team-switcher.svelte';
	import RecentSales from '$lib/components/recent-sales.svelte';
	import Transactions from '$lib/components/transactions.svelte';
	import Stats from '$lib/components/stats.svelte';
	import Overview from '$lib/components/overview.svelte';
	import SwapLayout from '$lib/components/swap-layout.svelte';
	import type { ComponentType } from 'svelte';

	const sections: Record<string, ComponentType> = {
		top: Stats,
		center_left: Overview,
		center_right: RecentSales,
		bottom: Transactions
	};

	const sectionSlotClassNames = {
		'1': 'col-span-2 row-span-1 h-full w-full flex flex-col',
		'2': 'col-span-1 row-span-2 h-full w-full flex flex-col',
		'3': 'col-span-1 row-span-2 h-full w-full flex flex-col',
		'4': 'col-span-2 row-span-2 h-full w-full flex flex-col'
	};

	function handleSwap(event: CustomEvent<Record<string, string | null>>) {
		console.log('Layout swapped:', event.detail);
	}
</script>

<main class="p-y-4 flex min-h-screen flex-col items-center justify-between">
	<div class="mx-auto flex w-full max-w-7xl flex-col">
		<div class="border-b">
			<div class="flex h-16 items-center px-4">
				<TeamSwitcher />
				<MainNav class="mx-6" />
				<div class="ml-auto flex items-center space-x-4">
					<Search />
					<UserNav />
				</div>
			</div>
		</div>
		<div class="flex-1 space-y-4 p-8 pt-6">
			<div class="flex flex-wrap items-center justify-between space-y-2">
				<h2 class="text-3xl font-bold tracking-tight">Dashboard</h2>
				<div class="flex items-center space-x-2">
					<CalendarDateRangePicker />
					<Button>Download</Button>
				</div>
			</div>
			<SwapLayout
				defaultEditing={false}
				{sections}
				{sectionSlotClassNames}
				class="grid w-full grid-cols-2 grid-rows-5 gap-8"
				on:swap={handleSwap}
			/>
		</div>
	</div>
</main>
