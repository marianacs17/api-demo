<template>
    <div>
        Listar

        <div class="card">
            <div class="card-header">
                Empleados
            </div>
            <div class="card-body">
                <table class="table">
                    <thead>
                        <tr>
                            <th>ID</th>
                            <th>Nombre</th>
                            <th>Correo</th>
                            <th>Acciones</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="empleado in empleados" :key="empleado.id">
                            //rows
                            <td>{{empleado.id}}</td>
                            <td>{{empleado.nombre}}</td>
                            <td>{{empleado.correo}}</td>
                            <td>
                                <a name="" id="" class="btn btn-primary" href="#" role="button">Crear</a>
                                <a name="" id="" class="btn btn-primary" href="#" role="button">Editar</a>
                                <a name="" id="" class="btn btn-primary" href="#" role="button">Listar</a>

                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    data(){

        return{
            empleados:[]
        }

    },


    created:function(){

        this.consultarEmpleados();

    },
    methods:{
        //
        consultarEmpleados(){
            fetch('http://localhost/phpmyadmin/index.php?route=/sql&db=empleados&table=empleados&pos=0')
            .then(respuesta=>respuesta.json())
            .then((datosRespuesta)=>{
                console.log(datosRespuesta)
                this.empleados=[]
                if(typeof datosRespuesta[0].success==='undefined')
                {
                    this.empleados=datosRespuesta;
                }
            })
            .catch(console.log)
        }
    }
}
</script>