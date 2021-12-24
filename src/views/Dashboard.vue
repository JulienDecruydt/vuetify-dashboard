<template>
    <div class="dashboard">
        <lastTask></lastTask>
        <h2>Suivi dossiers en cours</h2>
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
        <v-data-table :headers="headers" :items="data" :items-per-page="50" :single-expand="singleExpand" :expanded.sync="expanded">
            <template v-slot:item.cab="{ item }">
                <span class="cab" v-on:click="goCab(item.cab)">{{ item.cab }}</span>
            </template>
            <template v-slot:item.suivi="{ item }">
                <div class="rating__block">
                    <v-tooltip v-for="(r, index) in item.suivi" v-bind:key="index" tag="div" bottom>
                        <template v-slot:activator="{ on, attrs }">
                            <div v-bind="attrs" v-on="on" class="rating" :class="r.status" :title="r.title"></div>
                        </template>
                        <span>{{ r.title }}</span>
                    </v-tooltip>
                </div>
            </template>
            <template v-slot:item.actions="{ item }">
                <v-icon class="mr-2" @click="editItem(item)" title="Voir infos site">
                    mdi-pencil-outline
                </v-icon>
                <v-icon class="mr-2" @click="setHistory(item)" title="Historique">
                    mdi-history
                </v-icon>
            </template>
            <template v-slot:expanded-item="{ headers, item }">
                <td :colspan="headers.length">
                    <v-timeline class="timeline" dense clipped>
                        <v-timeline-item class="mb-4" v-for="(s, index) in item.suivi" v-bind:key="index" :color="colorSelector(s.status)" icon-color="grey darken-1" small>
                            <v-row>
                                <v-col cols="2">
                                    <span>{{ s.title }}</span>
                                    <br>
                                    <span>{{ s.ref }}</span>
                                </v-col>
                                <v-col class="text-right" cols="2">
                                    {{ s.updated }}
                                </v-col>
                            </v-row>
                        </v-timeline-item>
                    </v-timeline>
                </td>
            </template>
        </v-data-table>
        <hello-world v-if="ok" />
    </div>
</template>
<script>
import HelloWorld from '../components/HelloWorld'
import lastTask from '../components/lastTask'

export default {
    name: 'Dashboard',
    components: {
        HelloWorld,
        lastTask
    },
    data() {
        return {
            ok: false,
            expanded: [],
            singleExpand: true,
            headers: [
                { text: 'CAB', value: 'cab' },
                { text: 'Suivi étapes', value: 'suivi' },
                { text: 'Tâche en cours', value: 'task' },
                { text: 'Référent', value: 'ref' },
                { text: 'Création', value: 'created' },
                { text: '', value: 'actions' },
                { text: '', value: 'data-table-expand' },
            ],
            data: [{
                    id: 1,
                    cab: 'SEO63440',
                    task: 'Référencement',
                    ref: 'Boris Kopras',
                    suivi: [{
                            title: 'Création dossier',
                            status: 'finish',
                            ref: 'Person A',
                            updated: '06/08/2021 à 15h39'
                        },
                        {
                            title: 'Arborescence',
                            status: 'finish',
                            ref: 'Person A',
                            updated: '06/08/2021 à 15h39'
                        },
                        {
                            title: 'Référencement',
                            status: 'pending',
                            ref: 'Person A',
                            updated: ''
                        },
                        {
                            title: 'Livraison',
                            status: 'unfinish',
                            ref: '',
                            updated: ''
                        }
                    ],
                    created: '06/08/2021 à 15h39'
                },
                {
                    id: 2,
                    cab: 'SEO63440',
                    task: 'Arborescence du site',
                    ref: 'Boris Kopras',
                    suivi: [{
                            title: 'Création dossier',
                            status: 'finish',
                            ref: 'Person A',
                            updated: '06/08/2021 à 15h39'
                        },
                        {
                            title: 'Arborescence',
                            status: 'unfinish',
                            ref: '',
                            updated: ''
                        },
                        {
                            title: 'Référencement',
                            status: 'unfinish',
                            ref: '',
                            updated: ''
                        },
                        {
                            title: 'Livraison',
                            status: 'unfinish',
                            ref: '',
                            updated: ''
                        }
                    ],
                    created: '06/08/2021 à 15h39'
                },
                {
                    id: 3,
                    cab: 'SEO63440',
                    task: 'Arborescence du site',
                    ref: 'Boris Kopras',
                    suivi: [{
                            title: 'Création dossier',
                            status: 'finish',
                            ref: 'Person A',
                            updated: '06/08/2021 à 15h39'
                        },
                        {
                            title: 'Arborescence',
                            status: 'pending',
                            ref: 'Person A',
                            updated: ''
                        },
                        {
                            title: 'Référencement',
                            status: 'unfinish',
                            ref: '',
                            updated: ''
                        },
                        {
                            title: 'Livraison',
                            status: 'unfinish',
                            ref: '',
                            updated: ''
                        }
                    ],
                    created: '06/08/2021 à 15h39'
                },
                {
                    id: 4,
                    cab: 'SEO63440',
                    task: 'Livraison',
                    ref: 'Boris Kopras',
                    suivi: [{
                            title: 'Création dossier',
                            status: 'finish',
                            ref: 'Person A',
                            updated: '06/08/2021 à 15h39'
                        },
                        {
                            title: 'Arborescence',
                            status: 'finish',
                            ref: 'Person A',
                            updated: '06/08/2021 à 15h39'
                        },
                        {
                            title: 'Référencement',
                            status: 'finish',
                            ref: 'Person A',
                            updated: '06/08/2021 à 15h39'
                        },
                        {
                            title: 'Livraison',
                            status: 'finish',
                            ref: 'Person A',
                            updated: '06/08/2021 à 15h39'
                        }
                    ],
                    created: '06/08/2021 à 15h39'
                },
                {
                    id: 5,
                    cab: 'SEO63440',
                    task: 'Référencement',
                    ref: 'Boris Kopras',
                    suivi: [{
                            title: 'Création dossier',
                            status: 'finish',
                            ref: 'Person A',
                            updated: '06/08/2021 à 15h39'
                        },
                        {
                            title: 'Arborescence',
                            status: 'finish',
                            ref: 'Person A',
                            updated: '06/08/2021 à 15h39'
                        },
                        {
                            title: 'Référencement',
                            status: 'pending',
                            ref: 'Person A',
                            updated: ''
                        },
                        {
                            title: 'Livraison',
                            status: 'unfinish',
                            ref: '',
                            updated: ''
                        }
                    ],
                    created: '06/08/2021 à 15h39'
                },
                {
                    id: 6,
                    cab: 'SEO63440',
                    task: 'Référencement',
                    ref: 'Boris Kopras',
                    suivi: [{
                            title: 'Création dossier',
                            status: 'finish',
                            ref: 'Person A',
                            updated: '06/08/2021 à 15h39'
                        },
                        {
                            title: 'Arborescence',
                            status: 'finish',
                            ref: 'Person A',
                            updated: '06/08/2021 à 15h39'
                        },
                        {
                            title: 'Référencement',
                            status: 'pending',
                            ref: 'Person A',
                            updated: ''
                        },
                        {
                            title: 'Livraison',
                            status: 'unfinish',
                            ref: '',
                            updated: ''
                        }
                    ],
                    created: '06/08/2021 à 15h39'
                },
            ]
        }
    },
    methods: {
        setHistory(item) {
            if (this.expanded.includes(item)) {
                this.expanded.splice(this.expanded.indexOf(item), 1);
                return
            }
            this.expanded = []
            this.expanded.push(item)
        },
        colorSelector(status) {
            if (status == 'finish') {
                return '#43A047'
            }
            if (status == 'pending') {
                return '#1E88E5'
            }
            return '#757575'
        },
        goCab(cab) {
            this.$router.push({ path: '/cab/' + cab })
        }
    }
}
</script>
<style lang="scss" scoped>
.dashboard {
    .search__task {
        margin-top: 10px;
        border-radius: 5px 5px 0 0;
    }

    .timeline {
        margin-top: 15px;
    }

    .v-timeline {
        padding: 0;
    }

    .v-timeline-item {
        margin: 0 !important;
    }

    .v-tooltip {
        display: block;
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

    .cab {
        color: #1E88E5;
    }

    .v-card__title {
        justify-content: center;
    }

    .rating__block {
        display: flex;
        align-items: center;

        .rating {
            width: 10px;
            height: 10px;
            border: 2px solid #757575;
            margin-right: 10px;

            &.finish {
                background: #43A047;
                border-color: #43A047;
            }

            &.pending {
                background: #1E88E5;
                border-color: #1E88E5;
            }
        }
    }
}
</style>

<style>
    tr.v-data-table__expanded__content {
        box-shadow: none !important;
    }
</style>