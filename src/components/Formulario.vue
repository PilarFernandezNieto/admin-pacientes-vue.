<script setup>
    import {reactive} from "vue";
    import Alerta from "./Alerta.vue";

    const alerta = reactive({
        tipo: "",
        mensaje: ""
    });

    const validar = (e) => {
      
        if(Object.values(paciente).includes("")){
           alerta.mensaje = "Todos los campos son obligatorios";
           alerta.tipo = "error";
           return;
           
        } 
        console.log('Agregando');
    }

    defineEmits(['update:nombre', 'update:propietario', 'update:email', 'update:alta', 'update:sintomas'])
    const props = defineProps({
        nombre: {
            type: String,
            required: true
        }
    })


</script>


<template>
    <!-- Componente: Formulario -->
    <div class="md:w-1/2">
        <h2 class="font-black text-3xl text-center">Seguimiento Pacientes</h2>

        <p class="text-lg mt-5 text-center mb-10">Añade pacientes y <span
                class="text-indigo-600 font-bold">Adminístralos</span></p>

        <Alerta v-if="alerta.mensaje" :alerta="alerta" />

        <form class="bg-white shadow-md rounded-lg py-10 px-5 mb-10 mx-5 md:mx-0" @submit.prevent="validar">

            <div class="mb-5">
                <label class="text-gray-700 uppercase font-bold" for="mascota">Nombre Mascota</label>
                <input type="text" id="mascota" class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
                    placeholder="Nombre de la mascota" @input="$emit('update:nombre', $event.target.value)">
            </div>
            <div class="mb-5">
                <label class="text-gray-700 uppercase font-bold" for="propietario">Nombre Propietario</label>
                <input type="text" id="propietario" class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
                    placeholder="Nombre del propietario" @input="$emit('update:propietario', $event.target.value)">
            </div>
            <div class="mb-5">
                <label class="text-gray-700 uppercase font-bold" for="email">Email</label>
                <input type="email" id="email" class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
                    placeholder="Email del propietario" @input="$emit('update:email', $event.target.value)">
            </div>
            <div class="mb-5">
                <label class="text-gray-700 uppercase font-bold" for="alta">Alta</label>
                <input type="date" id="alta" class="border-2 w-full p-2 mt-2 rounded-md"
                    @input="$emit('update:alta', $event.target.value)">
            </div>
            <div class="mb-5">
                <label class="text-gray-700 uppercase font-bold" for="sintomas">Síntomas</label>
                <textarea id="sintomas" placeholder="Describe los síntomas"
                    class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-40"
                    @input="$emit('update:sintomas', $event.target.value)"></textarea>

            </div>
            <input type="submit"
                class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-700 cursor-pointer transition-colors"
                value="Registrar Paciente">

        </form>
    </div>
</template>



