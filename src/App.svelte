<script>
	import Instruction from './comp/Instruction.svelte';
	import SignIn from './comp/Signin.svelte';
	import Addcat from './comp/Addcat.svelte';
	import ListCat from './comp/Listcat.svelte';
	import { loggedIn$ } from './Firebase.js';

	//Make something more observable
	const user = loggedIn$;
</script>


<div class="flex-row">
<div class="flex-column">
	<Instruction/>
	<SignIn user={user} />
	<div>
		<Addcat user={user} />
		<ListCat user={user} />
	</div>

	
</div>
</div>