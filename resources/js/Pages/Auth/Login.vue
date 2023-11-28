<script setup lang="ts">
import { Head, Link, useForm } from "@inertiajs/vue3";
import AppLayout from "@/Layouts/AppLayout.vue";
defineProps<{
    canResetPassword?: boolean;
    status?: string;
}>();

const form = useForm({
    email: "",
    password: "",
    remember: false,
});

const submit = () => {
    form.post(route("login"), {
        onFinish: () => {
            form.reset("password");
        },
    });
};
</script>
<template>
    <AppLayout>
        <Head title="Log in" />
        <v-app>
            <v-sheet width="300" class="mx-auto m-20 p-3">
                <div
                    v-if="status"
                    class="mb-4 font-medium text-sm text-green-600"
                >
                    {{ status }}
                </div>
                <v-form fast-fail @submit.prevent="submit">
                    <v-text-field
                        v-model="form.email"
                        label="Your Email"
                        :error-messages="form.errors.email"
                    ></v-text-field>

                    <v-text-field
                        v-model="form.password"
                        label="Your Password"
                        :error-messages="form.errors.password"
                    ></v-text-field>
                    <v-checkbox
                        v-model="form.remember"
                        label="Remeber me?"
                        required
                    ></v-checkbox>
                    <div class="flex items-center justify-end mt-4">
                        <Link
                            v-if="canResetPassword"
                            :href="route('password.request')"
                            class="underline text-sm text-gray-600 dark:text-gray-400 hover:text-gray-900 dark:hover:text-gray-100 rounded-md focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 dark:focus:ring-offset-gray-800"
                        >
                            Forgot your password?
                        </Link>

                        <PrimaryButton
                            class="ms-4 bd-primary"
                            :class="{ 'opacity-25': form.processing }"
                            :disabled="form.processing"
                        >
                            
                        </PrimaryButton>
                    </div>

                    <v-btn type="submit" block class="mt-2">Submit</v-btn>
                </v-form>
            </v-sheet>
        </v-app>
    </AppLayout>
</template>