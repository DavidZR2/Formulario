<script>
export default {
    data: () => ({
        proyecto: "",
        tipo: "",
        urgente: false,
        proyectos: [] ,
    }),
    methods: {
        registrarProyecto() {
            const proyecto= {
                proyecto: this.proyecto,
                tipo: this.tipo,
                urgente: this.urgente,
            };
            this.proyectos.push(proyecto);

            this.proyecto = "";
            this.tipo = "";
            this.urgente = false;
        },
    },
};
</script>

<template>
    <form @submit.prevent="registrarProyecto">
        <div class="mb-3">
            <label class="form-label"> Proyecto: </label>
            <input  v-model.trim="proyecto" class="form-control"  type="text" required />
        </div>

        <div class="mb-3">
            <label class="form-label">Actividad: </label>
            <select v-model.trim="tipo" class="form-select"  required>
                <option disabled selected value="">Selecciona un tipo de actividad</option>
                <option >Aplicaciones web con Vue.js</option>
                <option >Backend services con Node.js</option>
                <option >App movil con React Native</option>

            </select>
        </div>

        <div class="mb-3">
            <label for="exampleInputPassword1" class="form-check-label">Urgente</label>
            <input v-model="urgente" type="checkbox" class="form-check-input"  />
        </div>

        <button type="submit" class="btn btn-primary" >Guardar</button>
    </form>
    <hr>

    <div class="table-responsive">
        <table class="table table-white" table-hover>
            <thead>
                <tr>
                    <th>#</th>
                    <th>Proyecto</th>
                    <th>Tipo</th>
                    <th>Urgente</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(proyecto, index) in proyectos" :key="index">
                    <td>{{ index + 1}}</td>
                    <td>{{ proyecto.proyecto }}</td>
                    <td>{{ proyecto.tipo }}</td>
                    <td :class="proyecto.urgente ? 'bg-succes' : 'bg-danger' ">{{ proyecto.urgente ? "Si"  : "No" }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>