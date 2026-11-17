<script setup>
import AktorFilmowy from './AktorFilmowy.vue';
defineProps({daneFilmu:Object});
defineEmits(['usunFilm']);
</script>

<template>
    <tr>
        <td>
            {{ daneFilmu.tytul }}
            <AktorFilmowy :dane-aktora="daneFilmu.aktor"/>
        </td>
    <td><button @click="$emit('usunFilm',daneFilmu)">Usuń</button></td>
    </tr>
</template>