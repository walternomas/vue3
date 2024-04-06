<template>
    <section>
        <h3>Añadir Profesor</h3>
        <div><label>Nombre</label><input type="text" v-model="teacher.teacherName" /></div>
        <div><label>Apellido</label><input type="text" v-model="teacher.surname" /></div>
        <div><label>DNI</label><input type="text" v-model="teacher.dni" /></div>
        <div><label>Materias</label><input type="text" v-model="subject" /><button @click="handleSubject">Agregar</button></div>
        <div>
            <ul>
                <li v-for="(subject, i) in teacher.subjects" :key="i">{{ subject }}</li>
            </ul>
        </div>
        <input type="checkbox" v-model="teacher.doc" />Documentación Entregada
        <button @click="handleAddTeacher">Agregar</button>
    </section>
    <section>
        <h3>Listado de profesores</h3>
        <table>
            <tr>
                <th>Nombre</th>
                <th>Apellido</th>
                <th>DNI</th>
                <th>Materias</th>
                <th>Documentación Entregada</th>
            </tr>
            <tr v-for="elm in teachers" :key="elm.dni">
                <th>{{ elm.teacherName }}</th>
                <th>{{ elm.surname }}</th>
                <th>{{ elm.dni }}</th>
                <th>
                    <ul>
                        <li v-for="(item,i) in elm.subjects" :key="i">{{ item }}</li>
                    </ul>
                </th>
                <th v-if="elm.doc">Entregada</th>
                <th v-else>No Entregada</th>
            </tr>
        </table>
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

    const handleSubject = () => {
        teacher.value.subjects.push(subject.value)
        subject.value=''
    }

    const handleAddTeacher = () => {
        teachers.value.push(teacher.value)
        teacher.value.teacherName = ''
        teacher.value.surname = ''
        teacher.value.dni = ''
        teacher.value.subjects = []
        teacher.value.doc = false
    }
</script>

<style scoped>
</style>