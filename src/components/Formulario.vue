<script setup>

import { reactive, computed  } from 'vue'
import Alerta from './Alerta.vue'

const alerta = reactive({
    tipo: '',
    mensaje:''
})

const emit = defineEmits(['update:nombre', 'update:propietario', 'update:email', 'update:alta', 'update:sintomas', 'guardar-paciente'])

const props = defineProps({
    id: {
        id: [String, null],
        required: true
    },
    nombre: {
        nombre: String,
        required: true
    },
    propietario: {
        propietario: String,
        required: true
    },
    email: {
        email:String,
        required: true
    },
    convalidacion:{
        convalidacion: String,
        required: true
    },
    sintomas: {
        sintomas:String,
        required: true
    }
})


const validar = () => {
    
    if(Object.values(props).includes('')){
        alerta.mensaje = 'Todos los campos son obligatorios'
        alerta.tipo = 'error'

        setTimeout(() => {
            Object.assign(alerta,{
                tipo: '',
                mensaje: ''
            })
        }, 3000)
        
       return
    }
    
    emit('guardar-paciente')
        alerta.mensaje = 'Paciente se almaceno correctamente',
        alerta.tipo = 'exito'

        setTimeout(() => {
            Object.assign(alerta,{
                tipo: '',
                mensaje: ''
            })
        }, 3000)

    }

    const editando = computed(() => {
        return props.id
    })

</script>

<template>

    <div class="md:w-1/2">
        <h2 class="font-black text-3xl text-center"> Registra la informacion aqui</h2>

        <p class="text-lg mt-5 text-center mb-10">
            Añade Convalidaciones y 
            <span class="text-indigo-600 font-bold">Administralos</span>
        </p>

    <Alerta 
        v-if="alerta.mensaje"
        :alerta="alerta"
    />

    

        <form
        class="bg-gray-800 shadow-md rounded-lg py-10 px-5 mb-10 ml-10"
        @submit.prevent="validar"
        >

        <div class="mb-5">
            <label 
            for="mascota"
            class="block text-white uppercase font-bold"
            >
        Nombre del paciente 
        </label>
        <input
        id="mascota"
        type="text"
        placeholder="Nombre de La Mascota"
        class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
        :value="nombre"
        @input="$emit('update:nombre', $event.target.value)"
        />

        </div>

        <div class="mb-5">
            <label 
            for="propietario"
            class="block text-white uppercase font-bold"
            >
        Nombre del Recepcionista
        </label>
        <input
        id="propietario"
        type="text"
        placeholder="Nombre del Recepcionista"
        class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
        :value="propietario"
        @input="$emit('update:propietario', $event.target.value)"
        />

        </div>

        <div class="mb-5">
            <label 
            for="email"
            class="block text-white uppercase font-bold"
            >
        Email
        </label>
        <input
        id="email"
        type="email"
        placeholder="Email"
        class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
        :value="email"
        @input="$emit('update:email', $event.target.value)"
        />

        </div>

        <div class="mb-5">
            <label 
            for="alta"
            class="block text-white uppercase font-bold"
            >
        Fecha de la convalidacion
        </label>
        <input
        id="convalidacion"
        type="date"
        placeholder="Nombre de La Mascota"
        class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
        :value="alta"
        @input="$emit('update:convalidacion', $event.target.value)"
        />
        </div>

        <div class="mb-5">
            <label 
            for="sintomas"
            class="block text-white uppercase font-bold"
            >
        Anotaciones  
        </label>
        <textarea
        id="sintomas"
        placeholder="Resaltar un hecho importante (Se firmo, se reviso, etc...)"
        class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-40"
        :value="sintomas"
        @input="$emit('update:sintomas', $event.target.value)"
        />

        </div>
    <input
    type="submit"
    class="bg-indigo-600 w-full text-white uppercase font-bold hover:bg-indigo-700 cursor-pointer transition-colors h-10"
    :value="[editando ? 'Guardar Cambios' : 'Registrar Paciente']"    
    />
    
    </form>

    </div>

</template>