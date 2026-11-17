<script setup>
import {ref} from 'vue'
import UlubionyFilm from './components/UlubionyFilm.vue';
const filmy = ref([]);
let film_id = 0;
const nowyFilm = ref("");
const imieAktora = ref("");
const nazwiskoAktora= ref("");

filmy.value.push({
  id: film_id++,
  tytul:"Głupi i głupszy",
  aktor: {imieAktora:"Jim", nazwiskoAktora: "Carrey"}
})

function dodajNowyFilm(tytul, imie, nazwisko)
{
if (tytul!=""){
  filmy.value.push({
    id:film_id++,
    tytul:tytul,
    aktor: {imieAktora:imie, nazwiskoAktora:nazwisko}
  });
}
}

function usunFilm(film)
{
  filmy.value.splice(filmy.value.indexOf(film),1);
}

</script>

<template>
  <table class="table table-striped table-hover">
    <thead>
      <tr><th colspan="2">Lista filmów</th></tr>
    </thead>
    <tbody>
      <UlubionyFilm v-for="film in filmy" :key="film.id" :dane-filmu="film" @usunFilm="usunFilm">
      </UlubionyFilm>  
        
      
    </tbody>
    <tfoot>
      <tr>
        <td>
         <input v-model="nowyFilm" placeholder="Dopisz nowy film">
         <input v-model="imieAktora" placeholder="Wpisz imie aktora">
         <input v-model="nazwiskoAktora" placeholder="Wpisz nazwisko aktora">
        </td>
        <td>
          <button @click="dodajNowyFilm(nowyFilm, imieAktora, nazwiskoAktora)">Dodaj</button>
          </td>
      </tr>
    </tfoot>

  </table>
</template>
