<svelte:head>
	<title>Inventories</title>
	<meta name="Inventories" content="All the inventories" />
</svelte:head>

<script>
// @ts-nocheck

import { Table, TableBody, TableBodyCell, TableBodyRow, TableHead, TableHeadCell, TableSearch } from 'flowbite-svelte';
let searchTerm = '';
let items = [
    { id: 1, user: 'DrBlury', spaceX: 8, spaceY: 20 },
	{ id: 2, user: 'SomeUser', spaceX: 6, spaceY: 10 },
	{ id: 3, user: 'AnotherUser', spaceX: 5, spaceY: 12 }
];
$: filteredItems = items.filter((item) => item.user.toLowerCase().indexOf(searchTerm.toLowerCase()) !== -1);
</script>

<div class="text-column">
	<h1>Inventories:</h1>

	<TableSearch placeholder="Search by maker name" hoverable={true} bind:inputValue={searchTerm}>
		<TableHead>
			<TableHeadCell>ID</TableHeadCell>
			<TableHeadCell>User</TableHeadCell>
			<TableHeadCell>Space X</TableHeadCell>
			<TableHeadCell>Space Y</TableHeadCell>
		</TableHead>
		<TableBody class="divide-y">
			{#each filteredItems as item}
			<TableBodyRow>
			<TableBodyCell>{item.id}</TableBodyCell>
			<TableBodyCell>{item.user}</TableBodyCell>
			<TableBodyCell>{item.spaceX}</TableBodyCell>
			<TableBodyCell>{item.spaceY}</TableBodyCell>
			</TableBodyRow>
			{/each}
		</TableBody>
	</TableSearch>
</div>
