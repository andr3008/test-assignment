<template>
	<v-app>
		<v-main>
			<Searchbar />
		</v-main>
	</v-app>
</template>

<script>
import Searchbar from "./components/Searchbar";

export default {
	name: "App",

	components: {
		Searchbar,
	},
};
</script>
