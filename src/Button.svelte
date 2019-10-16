<style>
    button {
        width: 80%;
        margin: 0 10% 0 10%;
        height: 2rem;
        font: inherit;
        padding: 0.15rem 0.5rem;
        border: 1px solid #d10057;
        background-color: #d10057;
        color: white;
        cursor: pointer;
    }

    button:hover,
    button:active {
        box-shadow: 1px 1px 6px rgba(0, 0, 0, 0.26);
    }
</style>
<button on:click>
    <slot />
</button>