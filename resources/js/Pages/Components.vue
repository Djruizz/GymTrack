<script setup>
import { ref } from 'vue';
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import Checkbox from '@/Components/Checkbox.vue';
import DangerButton from '@/Components/DangerButton.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import Modal from '@/Components/Modal.vue';
import NavLink from '@/Components/NavLink.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';
import SecondaryButton from '@/Components/SecondaryButton.vue';
import TextInput from '@/Components/TextInput.vue';

const checked = ref(false);
const name = ref('');
const showModal = ref(false);
</script>

<template>
    <Head title="Componentes" />

    <AuthenticatedLayout>
        <div class="p-6 space-y-6">
            <h1 class="text-2xl font-semibold">Vista de componentes</h1>

            <section class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <div class="p-4 border rounded space-y-3">
                    <h2 class="font-medium">Logotipo</h2>
                    <div class="w-24 h-24">
                        <ApplicationLogo />
                    </div>
                </div>

                <div class="p-4 border rounded space-y-3">
                    <h2 class="font-medium">Botones</h2>
                    <div class="flex gap-2">
                        <PrimaryButton>Primary</PrimaryButton>
                        <SecondaryButton>Secondary</SecondaryButton>
                        <DangerButton>Danger</DangerButton>
                    </div>
                </div>

                <div class="p-4 border rounded space-y-3">
                    <h2 class="font-medium">Navegación</h2>
                    <div class="space-y-2">
                        <NavLink href="#">NavLink</NavLink>
                        <ResponsiveNavLink href="#">ResponsiveNavLink</ResponsiveNavLink>
                    </div>
                </div>
            </section>

            <section class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="p-4 border rounded space-y-3">
                    <h2 class="font-medium">Formulario</h2>

                    <InputLabel for="name" value="Nombre" />
                    <TextInput id="name" v-model="name" class="mt-1 block w-full" />
                    <InputError :message="name ? '' : 'El nombre es obligatorio' " />

                    <div class="pt-3">
                        <label class="flex items-center gap-2">
                            <Checkbox v-model="checked" />
                            <span>Acepto términos</span>
                        </label>
                    </div>
                </div>

                <div class="p-4 border rounded space-y-3">
                    <h2 class="font-medium">Dropdown & Links</h2>

                    <Dropdown>
                        <template #trigger>
                            <button class="px-3 py-2 rounded bg-gray-100">Abrir dropdown</button>
                        </template>

                        <div class="py-1">
                            <DropdownLink href="#">Perfil</DropdownLink>
                            <DropdownLink href="#">Ajustes</DropdownLink>
                            <DropdownLink href="#">Cerrar sesión</DropdownLink>
                        </div>
                    </Dropdown>

                    <div class="pt-3">
                        <a href="#" class="text-sm text-gray-600">Enlace normal</a>
                    </div>
                </div>
            </section>

            <div class="pt-4">
                <PrimaryButton @click="showModal = true">Abrir Modal</PrimaryButton>
            </div>
        </div>

        <Modal :show="showModal" @close="showModal = false">
            <template #title>Ejemplo de modal</template>
            <template #content>
                <p>Contenido del modal. Usa este modal para probar estilos.</p>
            </template>
            <template #footer>
                <SecondaryButton @click="showModal = false">Cerrar</SecondaryButton>
                <PrimaryButton @click="showModal = false">Aceptar</PrimaryButton>
            </template>
        </Modal>
    </AuthenticatedLayout>
</template>
