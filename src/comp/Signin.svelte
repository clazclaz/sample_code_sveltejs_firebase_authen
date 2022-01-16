<script>
    import firebase, { app } from '../Firebase';

    export let user;

    const signIn = () => {
        const authProvider = new firebase.auth.GoogleAuthProvider();
        app.auth().signInWithPopup(authProvider);
    }

    const signOut = async () => {
        await firebase.auth().signOut();
    }
</script>

<div class="flex-column">
    {#if $user}
        <h1>Welcome {$user.email}</h1>
            <ul>
                <li>{$user.displayName}</li>
                <li>{$user.email}</li>
                <li>{$user.emailVerified}</li>
                <li>{$user.metadata.lastSignInTime}</li>
                <li>{$user.phoneNumber}</li>
                <li>{$user.uid}</li>
            </ul>
        <button class="myButton" on:click={signOut}>Sign Out</button>
    {:else}
        <button class="myButton" on:click={signIn}>Sign In</button>
    {/if}
</div>