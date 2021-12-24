<template>
    <v-app>
        <v-app-bar class="top__bar" app>
            <router-link to="/" class="d-flex align-center">
                <v-toolbar-title>NOVA<span>BOARD</span></v-toolbar-title>
            </router-link>
            <v-spacer></v-spacer>
            <v-text-field prepend-inner-icon="mdi-magnify" class="cab__search" placeholder="Rechercher CAB, organisation ou site web" flat solo-inverted hide-details dense></v-text-field>
            <v-spacer></v-spacer>
            <v-select class="dash__selector" :items="['Référencement', 'Rédaction', 'Suivi']" label="Choix Dashboard" dense solo flat></v-select>
            <v-spacer></v-spacer>
            <v-badge content="6" offset-y="20" offset-x="20" :value="visible" bordered bottom overlap>
                <v-btn icon>
                    <v-icon>mdi-bell-outline</v-icon>
                </v-btn>
            </v-badge>
        </v-app-bar>
        <v-navigation-drawer class="navigation__left" fixed expand-on-hover clipped>
            <v-list-item nav dense two-line>
                <v-list-item-avatar size="30">
                    <img src="https://randomuser.me/api/portraits/men/30.jpg">
                </v-list-item-avatar>
                <v-list-item-content>
                    <v-list-item-title>John Doe</v-list-item-title>
                    <v-list-item-subtitle>Super admin</v-list-item-subtitle>
                </v-list-item-content>
            </v-list-item>
            <v-divider></v-divider>
            <v-list nav dense>
                <v-list-item v-on:click="$router.push({path : '/'})" link>
                    <v-list-item-icon>
                        <v-icon>mdi-view-dashboard-outline</v-icon>
                    </v-list-item-icon>
                    <v-list-item-title>Dashboard</v-list-item-title>
                </v-list-item>
                <v-list-item link>
                    <v-list-item-icon>
                        <v-icon>mdi-share-variant-outline</v-icon>
                    </v-list-item-icon>
                    <v-list-item-title>Espace collaboratif</v-list-item-title>
                </v-list-item>
                <v-list-item link>
                    <v-list-item-icon>
                        <v-icon>mdi-account-cog-outline</v-icon>
                    </v-list-item-icon>
                    <v-list-item-title>Gérer les utilisateurs</v-list-item-title>
                </v-list-item>
            </v-list>
            <v-divider></v-divider>
            <v-list nav dense>
                <v-list-item link>
                    <v-list-item-icon>
                        <v-badge color="blue darken-1" content="6" :value="true" bordered bottom overlap>
                            <v-icon color="blue darken-1">mdi-square-medium-outline</v-icon>
                        </v-badge>
                    </v-list-item-icon>
                    <v-list-item-title>En cours</v-list-item-title>
                </v-list-item>
                <v-list-item link>
                    <v-list-item-icon>
                        <v-badge color="green darken-1" content="50" :value="true" bordered bottom overlap>
                            <v-icon color="green darken-1">mdi-square-medium-outline</v-icon>
                        </v-badge>
                    </v-list-item-icon>
                    <v-list-item-title>Terminées</v-list-item-title>
                </v-list-item>
                <v-list-item link>
                    <v-list-item-icon>
                        <v-badge color="orange darken-1" content="10" :value="true" bordered bottom overlap>
                            <v-icon color="orange darken-1">mdi-square-medium-outline</v-icon>
                        </v-badge>
                    </v-list-item-icon>
                    <v-list-item-title>En contrôle</v-list-item-title>
                </v-list-item>
                <v-list-item link>
                    <v-list-item-icon>
                        <v-badge color="red darken-1" content="" :value="false" bordered bottom overlap>
                            <v-icon color="red darken-1">mdi-square-medium-outline</v-icon>
                        </v-badge>
                    </v-list-item-icon>
                    <v-list-item-title>Réfusées</v-list-item-title>
                </v-list-item>
            </v-list>
            <v-divider></v-divider>
            <v-list nav dense>
                <v-list-item v-on:click="$router.push({path : '/'})" link>
                    <v-list-item-icon>
                        <v-icon>mdi-logout</v-icon>
                    </v-list-item-icon>
                    <v-list-item-title>Se déconnecter</v-list-item-title>
                </v-list-item>
            </v-list>
        </v-navigation-drawer>
        <v-main class="main">
            <router-view />
        </v-main>
    </v-app>
</template>
<script>
export default {
    name: 'App',
    data: () => ({
        visible: true,
        dialog: false
    }),
};
</script>
<style lang="scss" scoped>
.top__bar {
    a {
        color: black;
        text-decoration: none;
        font-weight: bolder;

        span {
            color: #1E88E5;
        }
    }

    .cab__search {
        width: 70% !important;
    }

    .dash__selector {
        margin-top: 25px;
        max-width: 250px;
    }
}

.navigation__left {
    background: white !important;
    top: 65px !important;

    .v-list-item__title {}
}

.main {
    padding: 85px 20px 0 85px !important;
}
</style>
<style lang="scss">
.v-btn--has-bg {
    color: white !important;
}
</style>