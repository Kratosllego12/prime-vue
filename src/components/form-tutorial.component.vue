<template>
  <Form v-slot="$form" @submit.prevent="handleRegister" >
    <h1>Learning Center</h1>

    <div>
      <p>Titulo del Tutorial:</p>
      <Textarea v-model="titulo" :mixlength="5" type="text"/>
    </div>

    <div>
      <p>Descripcion:</p>
      <Textarea v-model="descripcion" :maxlength="500" type="text"/>
    </div>

    <div class="card flex justify-center">
      <p>Categoria:</p>
      <div class="flex flex-col gap-1">
        <Select v-model="categoria" type="text" name="job.name" required :options="jobs" optionLabel="name" placeholder="Selecciona una categoria"/>
      </div>
    </div>

    <div>
      <p>Dificultad:</p>
      <RadioButtonGroup v-model="dif" name="difficulty" class="flex flex-wrap gap-4">
        <div class="flex items-center gap-2">
          <RadioButton inputId="begginer" id="begginer" value="Begginer" />
          <label for="Begginer">Begginer</label>
        </div>
        <div class="flex items-center gap-2">
          <RadioButton inputId="intermediate" id="intermediate" value="Intermediate" />
          <label for="Intermediate">Intermediate</label>
        </div>
        <div class="flex items-center gap-2">
          <RadioButton inputId="advanced" id="advanced" value="Advanced" />
          <label for="Advanced">Advanced</label>
        </div>
      </RadioButtonGroup>
    </div>

    <div class="flex-auto">
      <p>Duracion: (Minutos)</p>
      <InputNumber v-model="duracion" :min="5" :max="600" inputId="dura" />
    </div>

    <div>
      <p>Instructor:</p>
      <Textarea v-model="instructor" type="text"/>
    </div>

    <div>
      <p>Dia de Publicacion:</p>
      <DatePicker v-model="day" type="text" required/>
    </div>

    <div class="flex items-center gap-2">
      <Checkbox v-model="statu" inputId="estado" value="Publicado" />
      <label for="status"> Publicado </label>
    </div>

    <div class="flex items-center gap-2">
      <p>Calificacion:</p>
      <Rating v-model="statu" />
    </div>

    <Button type="submit" @click="validarSeleccion" severity="secondary" label="Save" />
    <Button type="reset" label="Cancel" />
  </Form>
</template>

<script setup>
import Select from 'primevue/select';
import Button from 'primevue/button';
import RadioButton from "primevue/radiobutton";
import RadioButtonGroup from "primevue/radiobuttongroup";
import InputNumber from "primevue/inputnumber";
import Textarea from "primevue/textarea";
import DatePicker from "primevue/datepicker";
import Checkbox from "primevue/checkbox";
import Rating from "primevue/rating";
import { ref } from 'vue'

const titulo = ref(null)
const descripcion = ref(null)
const dif = ref(null)
const duracion = ref(null)
const instructor = ref(null)
const day = ref(null)
const statu = ref(null)
const calificacion = ref(null)
const categoria = ref(null)

const jobs = ref([
  { name: 'Programming', code: 'NY' },
  { name: 'Desing', code: 'RM' },
  { name: 'Marketing', code: 'LN' },
  { name: 'Architecture', code: 'IL' },
  { name: 'Databases', code: 'PS' },
])

const handleRegister = () => {
  if (categoria.value === null ) {
    alert('Falta elegir una categoria')
    return
  }
  if (dif.value === null ) {
    alert('Falta elegir una dificultad')
    return
  }
  if (day.value === null ) {
    alert('Falta elegir una fecha de publicacion')
    return
  }
  console.log('Registro:', {
    titulo: titulo.value,
    descripcion: descripcion.value,
    categoria: categoria.value,
    dif: dif.value,
    duracion: duracion.value,
    instructor: instructor.value,
    day: day.value,
    statu: statu.value,
    calificacion: calificacion.value,
  })
}

</script>

