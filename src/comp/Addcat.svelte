<script>
    import { firestore } from '../Firebase';
    
    export let user;

    const addCat = async () => {
        try {
            const value = 'New cat!';
            await firestore
                .collection('catfacts')
                .add({ test: 'new cat!', uid: $user.uid, catFacDate: new Date() })
        } catch (error) {
            console.error(error);
        }
    };

</script>


<div class="flex-column">
    {#if $user}
    <button className="myButton" on:click="{addCat}">
    2, Add Cat
    </button>
    {/if}
</div>