<template>
    <v-toolbar density="compact" :elevation="6">
        <v-toolbar-title class="text-secondary">Anqas</v-toolbar-title>

        <v-spacer></v-spacer>

        <template v-if="$page.props.auth.user">
            <v-btn icon>
                <v-icon>mdi-magnify</v-icon>
            </v-btn>

            <v-btn icon>
                <v-icon>mdi-heart</v-icon>
            </v-btn>

                <v-menu>
                    <template v-slot:activator="{ props }">
                        <v-btn icon="mdi-dots-vertical" v-bind="props"></v-btn>
                    </template>

                    <v-list>
                        <v-list-item>
                            <v-list-item-title>
                             <v-btn prepend-icon="mdi-logout" variant="text">
                                  <Link
                                    :href="route('logout')"
                                    method="post"
                                    as="button"
                                    >Logout</Link
                                >

                              </v-btn>

                            </v-list-item-title>
                            <v-list-item-title>
                           <v-btn
           prepend-icon="mdi-theme-light-dark"
            @click="toggleTheme"
            variant="text"
        > Theme</v-btn>

                            </v-list-item-title>
                        </v-list-item>
                    </v-list>
                </v-menu>

        </template>

        <template v-else>
            <v-btn variant="tonal" size="small" class="mr-5 bg-secondary">
                <Link :href="route('login')">Log in</Link>
            </v-btn>
        </template>
    </v-toolbar>
</template>
