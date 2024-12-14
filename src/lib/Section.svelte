<script>
    export let title;
    export let type;
    export let items;
</script>

<div class="section">
    <h4>{title} →</h4>
    <div class={type}>
        {#each items as item}
            <div class={type.slice(0, -1)}>
                <img src={item.img} alt={item.name} />
                <p>{item.name}</p>
                {#if item.link}
                    <p><a href={item.link} target="_blank">Join</a></p>
                {/if}
                {#if item.time}
                    <p>{item.time}</p>
                {/if}
                {#if item.duration}
                    <p>{item.duration}</p>
                {/if}
            </div>
        {/each}
    </div>
</div>
