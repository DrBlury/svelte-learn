<script lang="ts">
	import { writable } from 'svelte/store';
	import {
		type Node,
		type Edge,
		SvelteFlow,
		Controls,
		Background,
		BackgroundVariant,
		MiniMap
	} from '@xyflow/svelte';
	import ColorPickerNode from '../nodes/ColorPickerNode.svelte';
	import '@xyflow/svelte/dist/style.css';

	let nodes = writable<Node[]>([
		{
			id: '1',
			type: 'input',
			data: { label: 'Input Node' },
			position: { x: 0, y: 0 }
		},
		{
			id: '2',
			type: 'default',
			data: { label: 'Another Node' },
			position: { x: 200, y: 0 }
		},
		{
			id: '3',
			type: 'output',
			data: { label: 'Output Node' },
			position: { x: 400, y: 0 }
		},
		{
			id: '4',
			type: 'default',
			data: { label: 'Default Node' },
			position: { x: 200, y: 200 }
		},
		{
			id: '5',
			type: 'color-picker',
			data: { color: '#ff4000' },
			position: { x: 200, y: 400 }
		}
	]);

	let edges = writable<Edge[]>([
		{ id: 'e1-2', source: '1', target: '2', animated: true },
		{ id: 'e2-3', source: '2', target: '3', animated: true },
		{ id: 'e3-4', source: '3', target: '4', animated: true }
	]);

	const nodeTypes = {
		'color-picker': ColorPickerNode
	};
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Home site" />
</svelte:head>

<div style="height:100vh;">
	<SvelteFlow {nodes} {edges} {nodeTypes} fitView attributionPosition="top-right">
		<Controls />
		<Background variant={BackgroundVariant.Dots} />
		<MiniMap />
	</SvelteFlow>
</div>
