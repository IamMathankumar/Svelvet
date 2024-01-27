<script lang="ts">
	import Edge from "$lib/components/Edge/Edge.svelte";
    import EdgeButtons from "./EdgeButtons.svelte";
    import EdgeComponent from "./EdgeComponent.svelte";
	import { onDestroy } from "svelte";
	
	let mouseOver = false;
	let editable = false
	let path:string
	let edgehovering:any
	let hovering:any
	let edge:any
</script>

<Edge 
	bind:this={edge}
	let:path
	enableHover={true}
	let:hovering
	step
>
	{#if path && !path.includes("NaN")}
	<EdgeComponent on:edgeHovering={e=> edgehovering = e.detail} hovering={hovering} {path} />
	{/if}
	<div slot="label"  >
		
		
		<EdgeButtons  hovering={edgehovering} destroy={edge?.destroy} bind:mouseOver/>
		
	
	</div>
	
</Edge>
