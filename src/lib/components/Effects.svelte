<script>
    import { onMount } from "svelte";
    import clickSound from '$lib/files/audios/click.mp3'
    let  elapsed = $state(0);
    let interval = $state(1000);
    let audio = $state();

    onMount(()=>{
         audio  = new Audio();
         audio.src = clickSound;

         return ()=>{
            audio = undefined;
         }
     });
    $effect(()=> {
        const id = setInterval(()=>{
            elapsed += 1;
            if(elapsed > 10){
                elapsed = 0;
                audio.load();
                audio.play();
            }
        },interval);
        return()=>{
            clearInterval(id);
        };
    });

</script>

<button onclick={() => interval /= 2}>speed up</button>
<button onclick={() => interval *= 2}>slow down</button>

<p>elapsed: {elapsed}</p>
<p>interval: {interval}</p>