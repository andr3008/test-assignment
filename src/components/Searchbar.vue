<template>
	<v-container fluid fill-height class="green lighten-5">
		<v-row>
			<v-card class="mx-auto" width="60%" outlined>
				<v-card-title>Search People</v-card-title>
				<v-form class="d-flex flex-row mb-6">
					<v-text-field
						class="ml-8"
						color="grey"
						label="Filter text"
					></v-text-field>

					<v-btn class="mx-8 mt-2 grey--text">Search</v-btn>
				</v-form>
			</v-card>
		</v-row>

		<v-row class="mt-28 mb-12">
			<v-card class="mx-auto" width="60%" outlined>
				<v-card-title>Search Result</v-card-title>
				<v-data-table
					:headers="peopleHeaders"
					:items="people"
					:items-per-page="5"
					class="elevation-1"
				>
				</v-data-table>
			</v-card>
		</v-row>
	</v-container>
</template>

<script>
export default {
	name: "Searchbar",

	methods: {},

	data() {
		return {
			expanded: [],
			singleExpand: false,
			peopleHeaders: [
				{
					text: "Id",
					align: "start",
					value: "id",
				},

				{ text: "Firstname", value: "first_name" },
				{ text: "Lastname", value: "last_name" },
				{ text: "Email", value: "email" },
				{ text: "Gender", value: "gender" },
				{ text: "Phone", value: "phone" },
				{ text: "Language", value: "language" },
				{ text: "City", value: "city" },
				{ text: "", value: "data-table-expand" },
			],
			people: [
				{
					id: 1,
					first_name: "Barb",
					last_name: "Glewe",
					email: "bglewe0@netscape.com",
					gender: "Male",
					phone: "714-483-7786",
					language: "Tajik",
					city: "Sui’an",
				},
				{
					id: 2,
					first_name: "Harley",
					last_name: "Caistor",
					email: "hcaistor1@diigo.com",
					gender: "Male",
					phone: "440-572-0554",
					language: "Thai",
					city: "Piedrancha",
				},
				{
					id: 3,
					first_name: "Dunn",
					last_name: "Barsam",
					email: "dbarsam2@unicef.org",
					gender: "Male",
					phone: "441-362-5147",
					language: "Moldovan",
					city: "Topol’noye",
				},
			],
		};
	},
};
</script>
