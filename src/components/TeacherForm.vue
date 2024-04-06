<template>
    <section>
        <h3>Añadir Profesor</h3>
        <div><label>Nombre</label><input type="text" v-model="teacher.teacherName" /></div>
        <div><label>Apellido</label><input type="text" v-model="teacher.surname" /></div>
        <div><label>DNI</label><input type="text" v-model="teacher.dni" /></div>
        <div><label>Materias</label><input type="text" v-model="subject" /><button>Agregar</button></div>
        <input type="checkbox" v-model="teacher.doc" />Documentación Entregada
        <button>Agregar</button>
    </section>
    <section>
        <h3>Listado de profesores</h3>
    </section>
</template>

<script lang="ts" setup>
    import { Ref, ref } from 'vue';

    interface ITeacher {
        teacherName: string,
        surname: string,
        dni: string,
        subjects: Array<string>,
        doc: boolean
    }

    let teacher:Ref<ITeacher> = ref({
        teacherName: '',
        surname: '',
        dni: '',
        subjects: [],
        doc: false
    })

    let teachers:Ref<Array<ITeacher>> = ref([])

    let subject:Ref<string> = ref('')
</script>

<style scoped>
</style>