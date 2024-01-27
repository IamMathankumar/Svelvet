<script lang="ts">
	import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher()

  export let path: string;
  export let hovering:boolean;
  $: updateEdge(hovering)
  const updateEdge = (hovering:boolean) =>{    
    dispatch("edgeHovering", hovering)
  }

</script>

<defs>
  <marker
    id="endarrow"
    markerWidth="10"
    markerHeight="10"
    refX="0"
    refY="5"
    orient="auto"
    markerUnits="userSpaceOnUse"
  >
    <polygon points="0 0, 10 5, 0 10" />
  </marker>
</defs>
<path  d={path} class={hovering? "hover" : ''} marker-end="url(#endarrow)" />

<style>

.hover {
    stroke: blue;
    stroke-width: 3px;
    stroke-dasharray: 10;
    stroke-dashoffset: 500;
    animation: dash 5s infinite linear forwards;
  }
  path {
    stroke:  crimson;
    stroke-width: 3px;
    z-index: 100;
  }

  @keyframes dash {
    to {
      stroke-dashoffset: 0;
    }
  }
  polygon {
    fill: "#ff0000";
    stroke: "transparent";
    stroke-width: 3px;
  }

</style>
