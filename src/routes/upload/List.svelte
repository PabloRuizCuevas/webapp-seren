
<script lang="ts">

    export let files: Array<any>;
      
</script>


<ol class="rectangle-list">
    {#each files as item}
        <li><a href="/upload">{item.name}</a></li>
    {/each}
</ol>


<style>
    
    .rectangle-list a{
        position: relative;
        display: block;
        padding: .4em .4em .4em .8em;
        *padding: .4em;
        margin: .5em 0 .5em 0.5em;
        background: #ddd;
        color: #444;
        text-decoration: none;
        transition: all .3s ease-out;
    }

    .rectangle-list a:hover{
        background: #eee;
    }

    li {
        /* marker not support background */  
    }


    li::marker{
        /* marker not support background */
        position: absolute;
        left: -0.5em;
        top: 50%;
        margin-top: -1em;
        background: #fa8072;
        height: 2em;
        width: 2em;
        line-height: 2em;
        text-align: center;
        font-weight: bold;
    }

    .rectangle-list a:after{
        position: absolute;
        content: '';
        border: .5em solid transparent;
        left: -1em;
        top: 50%;
        margin-top: -.5em;
        transition: all .3s ease-out;
    }

    .rectangle-list a:hover:after{
        left: -.5em;
        border-left-color: #fa8072;
    }

</style>