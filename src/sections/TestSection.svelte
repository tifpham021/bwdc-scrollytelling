<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
</script>

<div>
    <Scroller layout="left">
        {#snippet sticky()}
            
        {/snippet}
    
        {#snippet scrolly()}
            <ArticleText>
                <h1>hello</h1>
            </ArticleText>
        {/snippet}
    </Scroller>
</div>