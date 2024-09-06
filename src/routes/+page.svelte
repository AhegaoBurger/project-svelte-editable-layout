<script>
	import { Button } from '$lib/components/ui/button';
	import {
		Card,
		CardContent,
		CardDescription,
		CardHeader,
		CardTitle
	} from '$lib/components/ui/card';

	// navigation components
	import { UserNav } from '$lib/components/user-nav';
	import { MainNav } from '$lib/components/main-nav';
	import { CalendarDateRangePicker } from '$lib/components/date-range-picker';

	// high level components
	import Search from '$lib/components/search.svelte';
	import TeamSwitcher from '$lib/components/team-switcher.svelte';
	import RecentSales from '$lib/components/recent-sales.svelte';
	import Transactions from '$lib/components/transactions.svelte';
	import Stats from '$lib/components/stats.svelte';
	import Overview from '$lib/components/overview.svelte';

	// Skeleton loaders
	// import StatsLoader from '$lib/components/stats-loader.svelte';
	// import SwapLayoutLoader from '$lib/components/swap-layout-loader.svelte';
	// import OverviewLoader from '$lib/components/overview-loader.svelte';
	// import RecentSalesLoader from '$lib/components/recent-sales-loader.svelte';
	// import TransactionsLoader from '$lib/components/transactions-loader.svelte';

	// this is the initial layout of the swap layout.
	const initialSwapSections = {
		top: (
			<Card class="h-full flex-grow">
				<CardHeader>
					<CardTitle>Stats</CardTitle>
				</CardHeader>
				<CardContent class="pl-2">
					<Suspense key={'stats'} fallback={<StatsLoader />}>
						<Stats />
					</Suspense>
				</CardContent>
			</Card>
		),
		center_left: (
			<Card class="h-full flex-grow">
				<CardHeader>
					<CardTitle>Overview</CardTitle>
				</CardHeader>
				<CardContent class="pl-2">
					<Suspense key={'overview'} fallback={<OverviewLoader />}>
						<Overview />
					</Suspense>
				</CardContent>
			</Card>
		),
		center_right: (
			<Card class="h-full flex-grow">
				<CardHeader>
					<CardTitle>Recent Sales</CardTitle>
					<CardDescription>You made 265 sales this month.</CardDescription>
				</CardHeader>
				<CardContent>
					<Suspense key={'recent-sales'} fallback={<RecentSalesLoader />}>
						<RecentSales />
					</Suspense>
				</CardContent>
			</Card>
		),
		bottom: (
			<Card class="h-full flex-grow">
				<CardHeader class="flex flex-row items-center">
					<div class="grid gap-2">
						<CardTitle>Transactions</CardTitle>
						<CardDescription>Recent transactions from your store.</CardDescription>
					</div>
				</CardHeader>
				<CardContent>
					<Suspense key={'transactions'} fallback={<TransactionsLoader />}>
						<Transactions />
					</Suspense>
				</CardContent>
			</Card>
		)
	};

	// this is the class names for the sections of the swap layout.
	const sectionSlotclasss = {
		'1': 'col-span-2 row-span-1 h-full w-full flex flex-col',
		'2': 'col-span-1 row-span-2 h-full w-full flex flex-col',
		'3': 'col-span-1 row-span-2 h-full w-full flex flex-col',
		'4': 'col-span-2 row-span-2 h-full w-full flex flex-col'
	};
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
				sections={initialSwapSections}
				{sectionSlotclasss}
				class="grid w-full grid-cols-2 grid-rows-5 gap-8"
			/>
		</div>
	</div>
</main>
