<script context="module">
    export async function load({fetch, page}) {
        await new Promise(resolve => setTimeout(resolve, 0))
        const id = page.params.id
        const res = await fetch(`https://jsonplaceholder.typicode.com/posts/${id}`)
        const guide = await res.json()
    
        if (res.ok) {
            return {
                props: 
                {
                    guide
                }
            }
        }
        return {
    
            status: 301,
        // error: new Error("Could not fetch the guide")
           redirect: "/guides"
        }
    }
    </script>

<script>
    export let guide
</script>

<div class="guides">

    <h2>{guide.title}</h2>
    <p>{guide.body}</p>
</div>


<style>

    .guides {

        margin-top: 40px;
        padding: 10px;
        border: 1px dotted rgba(255,255,255,0.1)
    }
</style>