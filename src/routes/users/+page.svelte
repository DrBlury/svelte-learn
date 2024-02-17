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
			type: 'admin',
			username: 'DrBlury',
			email: 'test@something.com',
			signupDate: '2023-01-01'
		},
		{
			id: 2,
			type: 'user',
			username: 'SomeUser',
			email: 'example@example.com',
			signupDate: '2023-01-01'
		},
		{
			id: 3,
			type: 'banneduser',
			username: 'AnotherUser',
			email: 'another@example.com',
			signupDate: '2023-01-01'
		}
	];
	$: filteredItems = items.filter(
		(item) => item.email.toLowerCase().indexOf(searchTerm.toLowerCase()) !== -1
	);
</script>

<svelte:head>
	<title>Users</title>
	<meta name="Users" content="All Users" />
</svelte:head>

<div class="text-column">
	<h1>Users:</h1>

	<TableSearch placeholder="Search by user email" hoverable={true} bind:inputValue={searchTerm}>
		<TableHead>
			<TableHeadCell>ID</TableHeadCell>
			<TableHeadCell>Username</TableHeadCell>
			<TableHeadCell>Email</TableHeadCell>
			<TableHeadCell>Signup</TableHeadCell>
		</TableHead>
		<TableBody class="divide-y">
			{#each filteredItems as item}
				<TableBodyRow>
					<TableBodyCell>{item.id}</TableBodyCell>
					<TableBodyCell>{item.username}</TableBodyCell>
					<TableBodyCell>{item.email}</TableBodyCell>
					<TableBodyCell>{item.signupDate}</TableBodyCell>
				</TableBodyRow>
			{/each}
		</TableBody>
	</TableSearch>
</div>
