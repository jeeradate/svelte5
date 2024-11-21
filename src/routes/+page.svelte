<script>
	import { onMount } from "svelte";
    import Effects from "$lib/components/Effects.svelte";
    let audio = $state();
    let count = $state(0);

     onMount(()=>{
         audio  = new Audio('click.mp3');
         return ()=>{
            audio = undefined;
         }
     });

    function onclick(){
        audio.load();
        audio.play();
        count++;
        if(count >5){
            count = 0;
        }
    }
</script>


<button {onclick}>
    clicks: {count}
</button>
<hr>
<div style="padding: 30px;">
    <h3>Effects Component</h3>
    <Effects />
</div>
