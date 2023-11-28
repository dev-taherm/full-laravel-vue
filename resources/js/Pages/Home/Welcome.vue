<script setup lang="ts">
import { Head } from "@inertiajs/vue3";
import AppLayout from "@/Layouts/AppLayout.vue";
import { ref } from "vue";

const tab = ref(null);
</script>

<template>
    <AppLayout>
        <Head title="Welcome" />
        <v-app>
            <v-card>
                <v-tabs v-model="tab" color="secondary" align-tabs="center">
                    <v-tab :value="1">Services</v-tab>
                    <v-tab :value="2">Services Requests</v-tab>
                </v-tabs>
                <v-window v-model="tab">
                    <v-window-item :value="1"> Services  </v-window-item>

                    <v-window-item :value="2"> Services Requests </v-window-item>
                </v-window>
            </v-card>
        </v-app>
    </AppLayout>
</template>
