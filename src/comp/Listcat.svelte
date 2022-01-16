<script>
    import { collectionData, firestore } from '../Firebase';
    import { startWith } from 'rxjs/operators';
    const catFactsRef = firestore.collection('catfacts');

    export let user;

    const catFacts = collectionData(
        catFactsRef.orderBy('catFacDate')
    ).pipe(startWith([]));
</script>

<div class="flex-column max-800">
    <h3>Firestore Collection "catfacts"</h3>
    <div>
        {#each $catFacts as catFact}
            <div>
                {#if $user && $user.uid === catFact.uid}
                    <span role="img" aria-label="fun-cat">MY CAT : {catFact.catFacDate}</span>
                {:else}
                    <span role="img" aria-label="fun-cat">OTHERS CAT</span>
                {/if}
                <span>{catFact.test}</span>
            </div>
        {/each}
    </div>
</div>