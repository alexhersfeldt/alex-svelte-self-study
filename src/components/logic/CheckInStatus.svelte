<script>

    let user = {checkedIn: false};
    export let kidImg
    export let name = "Billy Bob";
    function toggle() {
        user.checkedIn = !user.checkedIn;
    }

    let time;
    function updateTime() {
        time = new Date();
    }
</script>

{#if !user.checkedIn}
    <div>
        <img class="checkedOutImg" src={kidImg} alt={name}>
    </div>

    <p>{name} Is not currently checked in</p>
    <div class="button">
        <button on:click={toggle}>
            Check In
        </button>
    </div>



{:else}
    <div>
        <img class="checkedInImg" src={kidImg} alt={name}>
    </div>
    <p>{name} checked in at {time}</p>
    <div class="button">
        <button on:click={toggle} on:click={updateTime()}>
            Check Out
        </button>
    </div>



{/if}

<style>
    img {
        border-radius: 40px;
        height: 250px;
        width: 300px;
        border: 2px solid navy;
    }
    .checkedOutImg{
        opacity: 0.2;
    }
</style>
