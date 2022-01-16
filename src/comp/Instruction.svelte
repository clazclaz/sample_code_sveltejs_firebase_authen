<script>
    import { loggedIn$ } from '../Firebase.js';

    const user = loggedIn$;
</script>

INNER
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
    {/if}