<script setup lang="ts">
import ToolBar from "@/Components/Toolbar.vue";
import { Link } from "@inertiajs/vue3";
import { ref } from "vue";

const drawer = ref(true);
const rail = ref(true);
</script>

<template>
    <div>
        <ToolBar> </ToolBar>
        <v-divider></v-divider>
        <v-card>
            <v-layout>
                <v-navigation-drawer
                    class="bg-main mt-12"
                    v-model="drawer"
                    :rail="rail"
                    permanent
                    @click="rail = false"
                >
                    <template v-if="$page.props.auth.user">
                        <v-list-item
                            prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
                            :title="$page.props.auth.user.name"
                            nav
                        >
                            <template v-slot:append>
                                <v-btn
                                    variant="text"
                                    icon="mdi-chevron-left"
                                    @click.stop="rail = !rail"
                                ></v-btn>
                            </template>
                            
                        </v-list-item>
                    </template>
                    <template v-else>
                       <v-list-item
                            prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
                            title="Login"
                            nav
                        >
                            <template v-slot:append>
                                <v-btn
                                    variant="text"
                                    icon="mdi-chevron-left"
                                    @click.stop="rail = !rail"
                                ></v-btn>
                            </template>
                            
                        </v-list-item>
                    </template>

                    <v-divider></v-divider>

                    <v-list density="compact" nav>
                        <Link :href="route('home')">
                        <v-list-item
                            prepend-icon="mdi-home-city"
                            title="Home"
                            value="home"
                        > </v-list-item>
                        </Link>
                        <v-list-item
                            prepend-icon="mdi-account"
                            title="My Account"
                            value="account"
                        ></v-list-item>
                        <v-list-item
                            prepend-icon="mdi-account-group-outline"
                            title="Users"
                            value="users"
                        ></v-list-item>
                    </v-list>
                </v-navigation-drawer>
                <v-main ><slot> </slot></v-main>
            </v-layout>
        </v-card>
    </div>
</template>
