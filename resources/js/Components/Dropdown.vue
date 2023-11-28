<script setup lang="ts">
import { ref } from "vue";

const items = ref([
    { title: "Click Me" },
    { title: "Click Me" },
    { title: "Click Me" },
    { title: "Click Me 2" },
]);
const locations = ref(["top", "bottom", "start", "end", "center"]);
const location = ref("end");
</script>

<template>
    <v-menu :location="location">
        <template v-slot:activator="{ props }">
            <v-btn icon>
                <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
        </template>
        <v-list>
            <v-list-item v-for="(item, index) in items" :key="index">
                <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item>
        </v-list>
    </v-menu>
</template>
