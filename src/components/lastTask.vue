<template>
    <div class="last__task">
        <h2>Dernières activités</h2>
        <div class="filter__block">
            <v-text-field prepend-inner-icon="mdi-magnify" class="search__task" placeholder="Rechercher CAB" flat solo-inverted hide-details dense></v-text-field>
            <v-btn color="white" elevation="2">
                <v-icon class="mr-2">
                    mdi-filter-menu-outline
                </v-icon>Filtres
            </v-btn>
            <v-btn color="white" elevation="2">
                <v-icon class="mr-2" @click="editItem(item)" title="Voir infos site">
                    mdi-download
                </v-icon>
                Exporter
            </v-btn>
        </div>
        <v-data-table :headers="headers" :items="data" :items-per-page="50">
            <template v-slot:item.cab="{ item }">
                <span class="cab" v-on:click="goCab(item.cab)">{{ item.cab }}</span>
            </template>
            <template v-slot:item.statut="{ item }">
                <v-icon color="green" v-if="item.statut == 'valid' ">
                    mdi-check-circle
                </v-icon>
                <v-icon color="orange" v-if="item.statut == 'control' ">
                    mdi-eye-outline
                </v-icon>
                <v-icon color="red" v-if="item.statut == 'invalid' ">
                    mdi-close-circle-outline
                </v-icon>
            </template>
            <template v-slot:item.actions="{ item }">
                <v-icon v-on:clcik="edit(item)">mdi-pencil-outline</v-icon>
                <v-icon>mdi-delete-outline</v-icon>
                <!--<v-menu open-on-hover bottom left>
                    <template v-slot:activator="{ on, attrs }">
                        <v-btn dark icon v-bind="attrs" v-on="on">
                            <v-icon>mdi-dots-vertical</v-icon>
                        </v-btn>
                    </template>
                    <v-list>
                        <v-list-item>
                            <v-list-item-title v-on:clcik="edit(item)"><v-icon>mdi-pencil-outline</v-icon> Editer</v-list-item-title>
                        </v-list-item>
                        <v-list-item>
                            <v-list-item-title v-on:clcik="edit(item)"><v-icon>mdi-delete-outline</v-icon> Supprimer</v-list-item-title>
                        </v-list-item>
                    </v-list>
                </v-menu>-->
            </template>
        </v-data-table>
    </div>
</template>
<script>
export default {
    name: 'lastTask',
    data() {
        return {
            headers: [
                { text: 'Tâche en cours', value: 'task' },
                { text: 'CAB', value: 'cab' },
                { text: 'Référent', value: 'ref' },
                { text: 'Demandé par', value: 'by' },
                { text: 'Catégorie', value: 'categorie' },
                { text: 'Création', value: 'created' },
                { text: 'Statut', value: 'statut' },
                { text: '', value: 'actions' }
            ],
            data: [{
                    id: 0,
                    statut: 'valid',
                    by: 'Arnaud Liotard',
                    task: "Créer l'arborescence du site",
                    cab: 'SEO20510',
                    ref: 'Boris Kopras',
                    categorie: 'Net-linking',
                    created: '06/08/2021 à 15h39'
                },
                {
                    id: 1,
                    statut: 'control',
                    by: 'Arnaud Liotard',
                    task: "Régler le soucis de ref",
                    cab: 'SEO00023',
                    ref: 'Boris Kopras',
                    categorie: 'Référencement',
                    created: '06/08/2021 à 15h39'
                },
                {
                    id: 2,
                    statut: 'valid',
                    by: 'Arnaud Liotard',
                    task: "Finaliser le dossier ref avec le client",
                    cab: 'SEO53201',
                    ref: 'Boris Kopras',
                    categorie: 'Référencement',
                    created: '06/08/2021 à 15h39'
                },
                {
                    id: 3,
                    statut: 'invalid',
                    by: 'Arnaud Liotard',
                    task: "Sitemap à faire",
                    cab: 'SEO02360',
                    ref: 'Boris Kopras',
                    categorie: 'Référencement',
                    created: '06/08/2021 à 15h39'
                },
                {
                    id: 4,
                    statut: 'valid',
                    by: 'Arnaud Liotard',
                    task: "Google maps à remplir",
                    cab: 'SEO08380',
                    ref: 'Boris Kopras',
                    categorie: 'Maps',
                    created: '06/08/2021 à 15h39'
                },
            ]
        }
    },
    methods: {
        goCab(cab) {
            this.$router.push({ path: '/cab/' + cab })
        }
    }
}
</script>
<style lang="scss" scoped>
.last__task {
    margin-bottom: 20px;

    .search__task {
        margin-top: 10px;
        border-radius: 5px 5px 0 0;
    }
    .filter__block {
        display: flex;
        align-items: center;
        gap: 20px;
        .v-btn {
            margin-top: 10px;
            color: #616161 !important;
        }
    }
    h1 {
        margin: 0 0 15px 0;
    }

    .cab {
        color: #1E88E5;
    }
}
</style>