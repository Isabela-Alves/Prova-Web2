<script setup>
import MyTextInput from '../MyTextInput.vue';
import PrimaryButton from '../PrimaryButton.vue';
import { useForm } from '@inertiajs/vue3';

const emit = defineEmits(['playlist-added']);

const form = useForm({
    title: '',
});

function submit() {
    form.post(route('playlists.store'), {
        onSuccess: () => {
            form.reset();
            emit('playlist-added');
        },
    });
}
</script>

<template>
    <form @submit.prevent="submit">
        <fieldset class="border shadow-md p-2 rounded-md w-full m-auto">
            <legend class="font-bold">
                Add new Playlist
            </legend>
            <div>
                <MyTextInput v-model="form.title" label="Title" autofocus />
                <PrimaryButton>Save</PrimaryButton>
            </div>
        </fieldset>
    </form>
</template>

