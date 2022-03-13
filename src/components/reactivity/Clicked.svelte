<script>


    let count = 0;
    $: doubled = count * 2;
    $: if(count % 5 === 0 && count !== 0) {
        alert("The Count is now " + count + ", I show up every 5 clicks!");
    };
    $: if(count > 1) {
        const warningMessage = document.getElementById("warningMessage");
        warningMessage.innerHTML = "Ohh, You can click. Aren't You cool"
    }
    $: if(count > 9) {
        const warningMessage = document.getElementById("warningMessage");
        warningMessage.innerHTML = "Ok, I get it. You can click. Now please stop Clicking"
    };
    $: if(count > 19) {
        const warningMessage = document.getElementById("warningMessage");
        warningMessage.innerHTML = "I TOLD YOU TO STOP CLICKING"
    };

    function incrementCount() {
        count += 1;
    }
</script>

<button on:click={incrementCount}>
    Clicked {count} {count === 1 ? 'time' : 'times'}
</button>
<p id="warningMessage">I bet you can't click 20 times.</p>
{#if count > 9 && count < 20}
    <p>This is an easier wey to add condition dependent text (10+ clicks)</p>
{:else }
    {#if count > 19}
        <p>And this is an easier way to tell you to STOP PUSHING THE BUTTON!</p>
    {/if}
{/if}
<p>If you had clicked twice as fast you would have clicked {doubled} times</p>

