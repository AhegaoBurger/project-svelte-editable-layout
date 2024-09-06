<script lang="ts">
	import { cn } from '$lib/utils';
	import type { Props } from './index';

	type $$Props = Props;

	let className: $$Props['class'] = undefined;
</script>

<nav class={cn('flex flex-wrap items-center space-x-4 lg:space-x-6', className)} {...$$restProps}>
	<a href="/examples/dashboard" class="text-sm font-medium transition-colors hover:text-primary">
		Overview
	</a>
</nav>
