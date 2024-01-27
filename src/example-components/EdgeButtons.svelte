<script lang="ts">
  

    export let hovering: any;
    export let destroy: any;
    export let mouseOver: boolean = true;
    $: console.log("hovering :::", hovering);
    mouseOver = true;
    var timeOut: any;

    $: if (!hovering) {
        clearTimeout(timeOut);
        timeOut = setTimeout(myTimer, 500);
    }

    const handleMouseOver = () => {
        clearTimeout(timeOut);

        mouseOver = true;
    };

    const deleteConnection = () => {
        
        destroy();
    };
    const addMessage = () => {
        destroy();
      
    };

    function myTimer() {
        mouseOver = false;
    }
    const handleMouseOut = () => {
        clearTimeout(timeOut);
        timeOut = setTimeout(myTimer, 500);
    };
</script>

    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div
        on:mouseover={handleMouseOver}
        on:mouseout={handleMouseOut}
        on:blur={() => {}}
        on:focus={() => {}}
    >
     <button >Hello</button>
    </div>

