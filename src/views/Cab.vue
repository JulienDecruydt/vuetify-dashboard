<template>
	<div class="cab__view">
		<v-card class="top__cab" flat>
			<div>CAB : <span>{{cab}}</span> -</div>
			<a href="http://www.google.com" target="_blank">
				www.google.com
				<v-icon color="white">mdi-open-in-new</v-icon>
			</a>
			<v-spacer></v-spacer>
			<v-btn color="light-blue accent-2" elevation="2">Assigner tâche pour {{cab}}</v-btn>
		</v-card>
		<v-tabs class="tab__selector" v-model="tab">
			<v-tabs-slider></v-tabs-slider>
			<v-tab href="#tab-1">
				Infos générales
			</v-tab>
			<v-tab href="#tab-2">
				Production
			</v-tab>
			<v-tab href="#tab-3">
				Tâches
			</v-tab>
			<v-tab href="#tab-4">
				Arborescence
			</v-tab>
			<v-tab href="#tab-5">
				GMB
			</v-tab>
			<v-tab href="#tab-6">
				Logs
			</v-tab>
		</v-tabs>
		<v-tabs-items class="tab__item" v-model="tab">
			<v-tab-item value="tab-1">
				<v-row no-gutters>
					<v-col class="p-4" cols="2">
						<v-card class="info__card">
							<div class="pa-2 title">
								Client
							</div>
							<v-list>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>CAB</v-list-item-subtitle>
										<v-list-item-title>{{cab}}</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Nom</v-list-item-subtitle>
										<v-list-item-title>Kopras</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Prénom</v-list-item-subtitle>
										<v-list-item-title>Boris</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Type de client</v-list-item-subtitle>
										<v-list-item-title>Interne nova</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
							</v-list>
						</v-card>
						<v-btn class="utils__btn" color="green darken-3" elevation="2" block>NOWA</v-btn>
						<v-btn class="utils__btn" color="orange darken-3" elevation="2" block>NOVASEO</v-btn>
						<v-btn class="utils__btn" color="blue darken-3" elevation="2" block>CDC</v-btn>
						<v-card class="info__card">
							<div class="pa-2 title">
								Organisation
							</div>
							<v-list>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Métier</v-list-item-subtitle>
										<v-list-item-title class="info__value">Thérapeute</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Métier GMB</v-list-item-subtitle>
										<v-list-item-title class="info__value">---</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Prénom</v-list-item-subtitle>
										<v-list-item-title class="info__value">Boris</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Nom</v-list-item-subtitle>
										<v-list-item-title class="info__value">MONSIEUR KOPRAS BORIS</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>E-mail</v-list-item-subtitle>
										<v-list-item-title class="info__value"><a href="mailto:koprasb@cometik.com">koprasb@cometik.com</a></v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Téléphone</v-list-item-subtitle>
										<v-list-item-title class="info__value">05.53.06.94.65</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Adresse</v-list-item-subtitle>
										<v-list-item-title class="info__value">LIEU DIT PUYJOUBERT 34310 BRANTOME EN PERIGORD</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
							</v-list>
						</v-card>
					</v-col>
					<v-col class="p-4" cols="3">
						<v-card class="info__card">
							<div class="pa-2 title">
								Contrat
							</div>
							<v-list>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Statut du dossier</v-list-item-subtitle>
										<v-list-item-title class="info__value">
											<v-icon color="orange">mdi-square-medium-outline</v-icon> En litige
										</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Date de signature</v-list-item-subtitle>
										<v-list-item-title class="info__value">20/12/2020</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Url du site</v-list-item-subtitle>
										<v-list-item-title class="info__value"><a href="http://www.google.com" target="_blank">www.google.com</a></v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Mensualité</v-list-item-subtitle>
										<v-list-item-title class="info__value">300€/mois</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
							</v-list>
						</v-card>
						<v-card class="info__card">
							<div class="pa-2 title">
								GMB
							</div>
							<v-list>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Statut de validation</v-list-item-subtitle>
										<v-list-item-title class="info__value">
											<v-icon color="green">mdi-square-medium-outline</v-icon> Validée
										</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Demandé par</v-list-item-subtitle>
										<v-list-item-title class="info__value">
											John Doe
										</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
								<v-list-item>
									<v-list-item-content>
										<v-list-item-subtitle>Date de la demande</v-list-item-subtitle>
										<v-list-item-title class="info__value">
											21/12/2020
										</v-list-item-title>
									</v-list-item-content>
								</v-list-item>
							</v-list>
						</v-card>
					</v-col>
					<v-col class="p-4" cols="7">
						<v-card class="info__card">
							<div class="pa-2 title">
								Derniers tickets JiraSD
							</div>
							<v-list>
								<v-list-item>
									<v-data-table :headers="headers" :items="data" :items-per-page="50" hide-default-footer>
										<template v-slot:item.actions="{ item }">
											<v-icon class="mr-2" @click="editItem(item)" title="Voir infos site">
												mdi-pencil-outline
											</v-icon>
										</template>
									</v-data-table>
								</v-list-item>
							</v-list>
						</v-card>
						<v-card class="info__card">
							<div class="pa-2 title">
								Commentaires
							</div>
							<v-list>
								<v-list-item>
									<v-data-table :headers="headerstwo" :items="datatwo" :items-per-page="50" hide-default-footer>
										<template v-slot:item.actions="{ item }">
											<v-icon class="mr-2" @click="editItem(item)" title="Répondre">
												mdi-message-outline
											</v-icon>
										</template>
									</v-data-table>
								</v-list-item>
							</v-list>
						</v-card>
					</v-col>
				</v-row>				
			</v-tab-item>
		</v-tabs-items>
	</div>
</template>
<script>
export default {
	name: 'Cab',
	data() {
		return {
			cab: '',
			tab: null,
			headers: [
				{ text: 'Tâche en cours', value: 'task' },
				{ text: 'Référent', value: 'ref' },
				{ text: 'Catégorie', value: 'categorie' },
				{ text: 'Création', value: 'created' },
				{ text: 'Actions', value: 'actions' }
			],
			data: [{
					id: 0,
					task: "Créer l'arborescence du site",
					cab: 'SEO20510',
					ref: 'Boris Kopras',
					categorie: 'Net-linking',
					created: '06/08/2021 à 15h39'
				},
				{
					id: 1,
					task: "Régler le soucis de ref",
					cab: 'SEO00023',
					ref: 'Boris Kopras',
					categorie: 'Référencement',
					created: '06/08/2021 à 15h39'
				},
				{
					id: 2,
					task: "Finaliser le dossier ref avec le client",
					cab: 'SEO53201',
					ref: 'Boris Kopras',
					categorie: 'Référencement',
					created: '06/08/2021 à 15h39'
				},
				{
					id: 3,
					task: "Sitemap à faire",
					cab: 'SEO02360',
					ref: 'Boris Kopras',
					categorie: 'Référencement',
					created: '06/08/2021 à 15h39'
				},
				{
					id: 4,
					task: "Google maps à remplir",
					cab: 'SEO08380',
					ref: 'Boris Kopras',
					categorie: 'Maps',
					created: '06/08/2021 à 15h39'
				},
			],
			headerstwo: [
				{ text: 'Commentaire', value: 'com' },
				{ text: 'Référent', value: 'ref' },
				{ text: 'Création', value: 'created' },
				{ text: 'Actions', value: 'actions' }
			],
			datatwo: [{
					id: 0,
					com: "Problème vu avec le client sur son site, il est ravi",
					cab: 'SEO20510',
					ref: 'Boris Kopras',
					created: '06/08/2021 à 15h39'
				},
				{
					id: 1,
					com: "Le client appelle pour avoir des infos sur son ref, il dit qu'il n'est pas satisfait",
					cab: 'SEO00023',
					ref: 'Boris Kopras',
					created: '06/08/2021 à 15h39'
				}
			],
		}
	},
	created() {
		this.cab = this.$route.params.cab
	}
}
</script>
<style lang="scss" scoped>
.cab__view {
	.top__cab {
		display: flex;
		align-items: center;
		padding: 10px;
		font-size: 25px;
		font-weight: bold;
		a {
			text-decoration: none;
			margin-left: 5px;

			i {
				font-size: 16px;
			}
		}
	}

	.utils__btn {
		margin-top: 15px;
	}

	.row {
		.col {
			padding-right: 20px;

			.v-list-item {
				display: block
			}
		}
	}
	.tab__selector {
		margin-top: 10px;
	}
	.tab__item {
		background: transparent;
	}
	.info__card {
		margin: 20px 0;

		.title {
			border-radius: 5px 5px 0 0;
			background: white !important;
			padding-left: 15px !important;
		}

		.info__value {
			white-space: normal;
			display: flex;
			align-items: center;
		}

		.content__value {
			overflow: inherit;
			padding-left: 10px;
		}
	}
}
</style>