

<script lang="ts">
    import React, { SetStateAction } from "react";
    import AnotherSvelteComponent from "./AnotherSvelteComponent.svelte";


    export let reactCountState: number = 0;
    export let updateReactCountState: React.Dispatch<SetStateAction<number>>;


    let internalSvelteState: number = 0;


    const updateReactStateFromSvelte=()=> {
        updateReactCountState(prevState => prevState+1);
    }

</script>

<div>Hey ! I am from svelte component. I am to be used inside react.

<p>Count value: {reactCountState}</p>

<p>Internal svelte state: {internalSvelteState}</p>

<button on:click={()=> internalSvelteState++}>Increase internal state</button>

<button on:click={()=>updateReactStateFromSvelte()}>
    Update react state from svelte
</button>


<p>-------------------------------</p>
<AnotherSvelteComponent reactState={reactCountState}/>
</div>