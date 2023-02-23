
<script context="module">
    let totalCount = 0

    export function getTotalCount() {
        return totalCount
    }
</script>

<script>
    let count = 0

    function clickHandler() {
        count += 1
        totalCount += 1
    }
</script>

<h2>Count - {count}</h2>
<!--module context variables are not reactive-->
<h2>Total Count - {totalCount}</h2>
<button on:click={clickHandler}>Increment</button>