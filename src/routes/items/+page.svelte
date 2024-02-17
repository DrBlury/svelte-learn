<script>
	// @ts-nocheck

	import {
		Table,
		TableBody,
		TableBodyCell,
		TableBodyRow,
		TableHead,
		TableHeadCell,
		TableSearch
	} from 'flowbite-svelte';
	let searchTerm = '';
	let items = [
		{
			id: 1,
			name: 'Healing Potion',
			type: 'consumable',
			description: 'A potion that heals HP',
			value: 10
		},
		{ id: 2, name: 'Sword', type: 'weapon', description: 'A sword that deals damage', value: 20 },
		{ id: 3, name: 'Shield', type: 'armor', description: 'A shield that blocks damage', value: 30 },
		{ id: 4, name: 'Bow', type: 'weapon', description: 'A bow that deals damage', value: 40 }
	];
	$: filteredItems = items.filter(
		(item) => item.name.toLowerCase().indexOf(searchTerm.toLowerCase()) !== -1
	);
</script>

<svelte:head>
	<title>Items</title>
	<meta name="Items" content="All the Items" />
</svelte:head>

<div class="text-column">
	<h1>Impress:</h1>

	<p>
		<strong>Author:</strong> Julian Bensch
	</p>

	<TableSearch placeholder="Search by item name" hoverable={true} bind:inputValue={searchTerm}>
		<TableHead>
			<TableHeadCell>ID</TableHeadCell>
			<TableHeadCell>Name</TableHeadCell>
			<TableHeadCell>Type</TableHeadCell>
			<TableHeadCell>Description</TableHeadCell>
			<TableHeadCell>Value</TableHeadCell>
		</TableHead>
		<TableBody class="divide-y">
			{#each filteredItems as item}
				<TableBodyRow>
					<TableBodyCell>{item.id}</TableBodyCell>
					<TableBodyCell>{item.name}</TableBodyCell>
					<TableBodyCell>{item.type}</TableBodyCell>
					<TableBodyCell>{item.description}</TableBodyCell>
					<TableBodyCell>{item.value}</TableBodyCell>
				</TableBodyRow>
			{/each}
		</TableBody>
	</TableSearch>
</div>
