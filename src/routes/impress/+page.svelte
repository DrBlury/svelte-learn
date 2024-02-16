<svelte:head>
	<title>Impress</title>
	<meta name="Impress" content="Impress of this site" />
</svelte:head>

<script>
// @ts-nocheck

import { Table, TableBody, TableBodyCell, TableBodyRow, TableHead, TableHeadCell, TableSearch } from 'flowbite-svelte';
let searchTerm = '';
let items = [
    { id: 1, maker: 'Toyota', type: 'ABC', make: 2017 },
    { id: 2, maker: 'Ford', type: 'CDE', make: 2018 },
    { id: 3, maker: 'Volvo', type: 'FGH', make: 2019 },
    { id: 4, maker: 'Saab', type: 'IJK', make: 2020 }
];
$: filteredItems = items.filter((item) => item.maker.toLowerCase().indexOf(searchTerm.toLowerCase()) !== -1);
</script>

<div class="text-column">
	<h1>Impress:</h1>

	<p>
		<strong>Author:</strong> Julian Bensch
	</p>

	<TableSearch placeholder="Search by maker name" hoverable={true} bind:inputValue={searchTerm}>
		<TableHead>
			<TableHeadCell>ID</TableHeadCell>
			<TableHeadCell>Maker</TableHeadCell>
			<TableHeadCell>Type</TableHeadCell>
			<TableHeadCell>Make</TableHeadCell>
		</TableHead>
		<TableBody class="divide-y">
			{#each filteredItems as item}
			<TableBodyRow>
			<TableBodyCell>{item.id}</TableBodyCell>
			<TableBodyCell>{item.maker}</TableBodyCell>
			<TableBodyCell>{item.type}</TableBodyCell>
			<TableBodyCell>{item.make}</TableBodyCell>
			</TableBodyRow>
			{/each}
		</TableBody>
	</TableSearch>
</div>
