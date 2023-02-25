<script lang="ts">
    import Button from '../lib/components/button.svelte'

    let content = 'sd'

    function setContent(event){
        content = event.detail;
    }
</script>
<h1>Hello world {content}</h1>
<Button on:pippo={setContent} disableX="true" inputValue="ciao"/>
