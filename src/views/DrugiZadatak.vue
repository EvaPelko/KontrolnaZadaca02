<template>
	<v-container fill-height fluid class="background">
		<v-row align="center" justify="center">
			<v-col align="center" justify="center" cols="12">
				<v-card class="pa-3 mb-12" outlined width="600px">
					<v-card-subtitle align="left">Zadovoljavaju uvjete</v-card-subtitle>
					<v-card-text>
						<v-data-table :headers="zaglavlje" item-key="">
							<template v-slot:[`item.actions`]="{ item }">
								<v-icon dense>mdi-open-in-app</v-icon>
							</template>
						</v-data-table>
					</v-card-text>
				</v-card>
				<v-card class="pa-3" outlined width="600px">
					<v-card-subtitle align="left">Ne zadovoljavaju uvjete</v-card-subtitle>
					<v-card-text>
						<v-data-table :headers="zaglavlje" item-key="">
							<template v-slot:[`item.actions`]="{ item }">
								<v-icon dense>mdi-open-in-app</v-icon>
							</template>
						</v-data-table>
					</v-card-text>
				</v-card>
			</v-col>
			<detalji />
		</v-row>
	</v-container>
</template>
<script>
import { zaglavlje } from "@/store.js";
import Detalji from "@/components/Detalji.vue";

export default {
	name: "drugi-zadatak",
	components: {
		Detalji,
	},
	data() {
		return {
			zadovoljili: [],
			nisuZadovoljili: [],
			sviStudent: [],
			zaglavlje: zaglavlje,
		};
	},
	methods: {
		loadajStudente() {
			let student = JSON.parse(localStorage.getItem("studenti"));
			if (studenti && studenti.length > 0) {
				this.sviStudenti = [...studenti];
				this.zadovoljili = [...studenti];
				this.nisuZadovoljili = [...studenti];
			}
		}
	},
	created() {
		this.loadajStudente();
	}
};
</script>
