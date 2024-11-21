<script>
    let click = new Audio('click.mp3');
    let count = $state(0);
    import Effects from "$lib/components/Effects.svelte";
    function onclick(){
        click.play();
        count++;
        if(count >5){
            count = 0;
        }
    }
</script>


<button {onclick}>
    clikcs: {count}
</button>
<hr>
<div style="padding: 30px;">
    <h3>Effects Component</h3>
    <Effects />
</div>
