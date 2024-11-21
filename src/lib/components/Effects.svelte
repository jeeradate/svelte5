<script>
    let  elapsed = $state(0);
    let interval = $state(1000);
    let click = new Audio('click.mp3');

    $effect(()=> {
        const id = setInterval(()=>{
            elapsed += 1;
            if(elapsed >100){
                elapsed = 0;
                click.play();
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