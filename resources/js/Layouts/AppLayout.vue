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
       <slot></slot>
    </div>
</template>
