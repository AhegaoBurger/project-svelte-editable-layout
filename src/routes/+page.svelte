<!-- src/routes/+page.svelte -->
<script lang="ts">
	import { Button } from '$lib/components/ui/button';
	import * as Card from '$lib/components/ui/card';
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

	const sections = {
		top: Stats,
		center_left: Overview,
		center_right: RecentSales,
		bottom: Transactions
	};

	const sectionSlotClassNames = {
		'1': 'col-span-2 row-span-1 h-full w-full',
		'2': 'col-span-1 row-span-2 h-full w-full',
		'3': 'col-span-1 row-span-2 h-full w-full',
		'4': 'col-span-2 row-span-2 h-full w-full'
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
				{sectionSlotClassNames}
				class="grid w-full grid-cols-2 grid-rows-5 gap-8"
				on:swap={handleSwap}
			>
				<!-- <svelte:fragment slot="top">
					<Card.Root class="h-full flex-grow">
						<Card.Header>
							<Card.Title>Stats</Card.Title>
						</Card.Header>
						<Card.Content class="pl-2">
							<Stats />
						</Card.Content>
					</Card.Root>
				</svelte:fragment>

				<svelte:fragment slot="center_left">
					<Card.Root class="h-full flex-grow">
						<Card.Header>
							<Card.Title>Overview</Card.Title>
						</Card.Header>
						<Card.Content class="pl-2">
							<Overview />
						</Card.Content>
					</Card.Root>
				</svelte:fragment>

				<svelte:fragment slot="center_right">
					<Card.Root class="h-full flex-grow">
						<Card.Header>
							<Card.Title>Recent Sales</Card.Title>
							<Card.Description>You made 265 sales this month.</Card.Description>
						</Card.Header>
						<Card.Content>
							<RecentSales />
						</Card.Content>
					</Card.Root>
				</svelte:fragment>

				<svelte:fragment slot="bottom">
					<Card.Root class="h-full flex-grow">
						<Card.Header>
							<Card.Title>Transactions</Card.Title>
							<Card.Description>Recent transactions from your store.</Card.Description>
						</Card.Header>
						<Card.Content>
							<Transactions />
						</Card.Content>
					</Card.Root>
				</svelte:fragment> -->

				<Card.Root slot="top" class="h-full">
					<Card.Header>
						<Card.Title>Stats</Card.Title>
					</Card.Header>
					<Card.Content class="pl-2">
						<Stats />
					</Card.Content>
				</Card.Root>

				<Card.Root slot="center_left" class="h-full">
					<Card.Header>
						<Card.Title>Overview</Card.Title>
					</Card.Header>
					<Card.Content class="pl-2">
						<Overview />
					</Card.Content>
				</Card.Root>

				<Card.Root slot="center_right" class="h-full">
					<Card.Header>
						<Card.Title>Recent Sales</Card.Title>
						<Card.Description>You made 265 sales this month.</Card.Description>
					</Card.Header>
					<Card.Content>
						<RecentSales />
					</Card.Content>
				</Card.Root>
			</SwapLayout>
			<Card.Root class="h-full flex-grow">
				<Card.Header>
					<Card.Title>Transactions</Card.Title>
					<Card.Description>Recent transactions from your store.</Card.Description>
				</Card.Header>
				<Card.Content>
					<Transactions />
				</Card.Content>
			</Card.Root>
		</div>
	</div>
</main>
