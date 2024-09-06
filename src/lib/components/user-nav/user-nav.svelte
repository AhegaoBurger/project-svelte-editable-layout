<script>
	import { Avatar, AvatarImage, AvatarFallback } from '$lib/components/ui/avatar';
	import { Button } from '$lib/components/ui/button';
	import {
		DropdownMenu,
		DropdownMenuContent,
		DropdownMenuItem,
		DropdownMenuLabel,
		DropdownMenuSeparator,
		DropdownMenuShortcut,
		DropdownMenuTrigger,
		DropdownMenuGroup
	} from '$lib/components/ui/dropdown-menu';
</script>

<DropdownMenu>
	<DropdownMenuTrigger asChild>
		<Button variant="ghost" class="relative h-8 w-8 rounded-full">
			<Avatar class="h-8 w-8">
				<AvatarImage src="/avatars/01.png" alt="@shadcn" />
				<AvatarFallback>SC</AvatarFallback>
			</Avatar>
		</Button>
	</DropdownMenuTrigger>
	<DropdownMenuContent class="w-56" align="end" forceMount>
		<DropdownMenuLabel class="font-normal">
			<div class="flex flex-col space-y-1">
				<p class="text-sm font-medium leading-none">shadcn</p>
				<p class="text-xs leading-none text-muted-foreground">m@example.com</p>
			</div>
		</DropdownMenuLabel>
		<DropdownMenuSeparator />
		<DropdownMenuGroup>
			<DropdownMenuItem>
				Profile
				<DropdownMenuShortcut>⇧⌘P</DropdownMenuShortcut>
			</DropdownMenuItem>
			<DropdownMenuItem>
				Billing
				<DropdownMenuShortcut>⌘B</DropdownMenuShortcut>
			</DropdownMenuItem>
			<DropdownMenuItem>
				Settings
				<DropdownMenuShortcut>⌘S</DropdownMenuShortcut>
			</DropdownMenuItem>
			<DropdownMenuItem>New Team</DropdownMenuItem>
		</DropdownMenuGroup>
		<DropdownMenuSeparator />
		<DropdownMenuItem>
			Log out
			<DropdownMenuShortcut>⇧⌘Q</DropdownMenuShortcut>
		</DropdownMenuItem>
	</DropdownMenuContent>
</DropdownMenu>
