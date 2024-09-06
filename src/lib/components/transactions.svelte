<script>
	import {
		Table,
		TableHeader,
		TableBody,
		TableRow,
		TableHead,
		TableCell
	} from '$lib/components/ui/table';
	import { Badge } from '$lib/components/ui/badge';
</script>

<Table>
	<TableHeader>
		<TableRow>
			<TableHead>Customer</TableHead>
			<TableHead class="hidden xl:table-column">Type</TableHead>
			<TableHead class="hidden xl:table-column">Status</TableHead>
			<TableHead class="hidden xl:table-column">Date</TableHead>
			<TableHead class="text-right">Amount</TableHead>
		</TableRow>
	</TableHeader>
	<TableBody>
		<TableRow>
			<TableCell>
				<div class="font-medium">Liam Johnson</div>
				<div class="hidden text-sm text-muted-foreground md:inline">liam@example.com</div>
			</TableCell>
			<TableCell class="hidden xl:table-column">Sale</TableCell>
			<TableCell class="hidden xl:table-column">
				<Badge class="text-xs" variant="outline">Approved</Badge>
			</TableCell>
			<TableCell class="hidden md:table-cell lg:hidden xl:table-column">2023-06-23</TableCell>
			<TableCell class="text-right">$250.00</TableCell>
		</TableRow>
		<TableRow>
			<TableCell>
				<div class="font-medium">Olivia Smith</div>
				<div class="hidden text-sm text-muted-foreground md:inline">olivia@example.com</div>
			</TableCell>
			<TableCell class="hidden xl:table-column">Refund</TableCell>
			<TableCell class="hidden xl:table-column">
				<Badge class="text-xs" variant="outline">Declined</Badge>
			</TableCell>
			<TableCell class="hidden md:table-cell lg:hidden xl:table-column">2023-06-24</TableCell>
			<TableCell class="text-right">$150.00</TableCell>
		</TableRow>
		<TableRow>
			<TableCell>
				<div class="font-medium">Noah Williams</div>
				<div class="hidden text-sm text-muted-foreground md:inline">noah@example.com</div>
			</TableCell>
			<TableCell class="hidden xl:table-column">Subscription</TableCell>
			<TableCell class="hidden xl:table-column">
				<Badge class="text-xs" variant="outline">Approved</Badge>
			</TableCell>
			<TableCell class="hidden md:table-cell lg:hidden xl:table-column">2023-06-25</TableCell>
			<TableCell class="text-right">$350.00</TableCell>
		</TableRow>
		<TableRow>
			<TableCell>
				<div class="font-medium">Emma Brown</div>
				<div class="hidden text-sm text-muted-foreground md:inline">emma@example.com</div>
			</TableCell>
			<TableCell class="hidden xl:table-column">Sale</TableCell>
			<TableCell class="hidden xl:table-column">
				<Badge class="text-xs" variant="outline">Approved</Badge>
			</TableCell>
			<TableCell class="hidden md:table-cell lg:hidden xl:table-column">2023-06-26</TableCell>
			<TableCell class="text-right">$450.00</TableCell>
		</TableRow>
	</TableBody>
</Table>
