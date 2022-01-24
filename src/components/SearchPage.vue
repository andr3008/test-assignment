<template>
	<v-container fluid>
		<v-row class="mx-auto">
			<v-card class="mx-auto mt-6" width="80%" outlined>
				<v-card-title>Search People</v-card-title>
				<v-form class="d-flex flex-row mb-6">
					<v-text-field
						v-model="filterText"
						class="ml-8"
						color="grey"
						label="Filter text"
					></v-text-field>
					<v-btn class="mx-8 mt-2 grey--text" @click="search">Search</v-btn>
				</v-form>
			</v-card>
		</v-row>

		<v-row class="mt-12 mx-auto">
			<v-card class="mx-auto" width="80%" outlined>
				<v-card-title>Search Result</v-card-title>

				<v-data-table
					:headers="peopleHeaders"
					:items="people"
					:expanded.sync="expanded"
					:items-per-page="5"
					item-key="id"
					show-expand
					class="elevation-1"
					@click:row="openPopup"
				>
					<template v-slot:expanded-item="{ headers, item }">
						<td class="pt-4 mb-3" :colspan="headers.length">
							<PersonDetails
								name="readonlyDetails"
								v-bind:person="item"
								v-bind:editable="false"
							/>
						</td>
					</template>
				</v-data-table>
			</v-card>
		</v-row>
		<v-layout>
			<v-dialog v-model="dialog" persistent width="60%">
				<v-card>
					<v-card-title class="headline">Person Info</v-card-title>
					<td class="px-8 mb-3">
						<PersonDetails
							name="editableDetails"
							v-bind:person="selectedPerson"
							v-bind:editable="true"
						/>
					</td>
					<v-card-actions>
						<v-spacer></v-spacer>
						<v-btn @click.native="closePopup">Close</v-btn>
					</v-card-actions>
				</v-card>
			</v-dialog>
		</v-layout>
	</v-container>
</template>
<script>
import PersonDetails from "./PersonDetails";

export default {
	components: { PersonDetails },
	name: "SearchPage",

	methods: {
		openPopup(row) {
			this.selectedPerson = row;
			this.dialog = true;
		},
		closePopup() {
			this.dialog = false;
		},
		search() {
			fetch("db.json")
				.then(async (response) => {
					const data = await response.json();
					if (!response.ok) {
						const error = (data && data.message) || response.statusText;
						return Promise.reject(error);
					}

					if (this.filterText.length > 1) {
						this.people = data.people.filter((person) => {
							var matches = false;

							for (const value of Object.values(person)) {
								var valueStr;
								if (typeof str !== "string") {
									valueStr = value.toString();
								}
								matches = valueStr
									.toLowerCase()
									.includes(this.filterText.toLowerCase());
								if (matches) break;
							}
							return matches;
						});
					} else {
						this.people = data.people;
					}
				})
				.catch((error) => {
					this.errorMessage = error;
					console.error("There was an error!", error);
				});
		},
	},

	data() {
		return {
			expanded: [],
			singleExpand: false,
			dialog: false,
			selectedPerson: {},
			filterText: "",
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
			people: [],
		};
	},
};
</script>
