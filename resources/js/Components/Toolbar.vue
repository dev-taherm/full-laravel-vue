<script setup lang="ts">
import { Link } from "@inertiajs/vue3";
import { useTheme } from "vuetify";
const theme = useTheme();

function toggleTheme() {
    theme.global.name.value = theme.global.current.value.dark
        ? "light"
        : "dark";
}
</script>

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

            <v-btn icon>
                <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
        </template>

        <template v-else>
            <v-btn variant="tonal" size="small" class="mr-5 bg-secondary">
                <Link :href="route('login')">Log in</Link>
            </v-btn>
        </template>
        <v-btn icon="mdi-theme-light-dark" class="mr-5" @click="toggleTheme"></v-btn>
    </v-toolbar>
</template>
