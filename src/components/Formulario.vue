<template>
  <div>    
    <h2 class="mx-3" v-bind:style="{ color: azul}">Desafío número 3</h2>
        <div class="m-3">
        <h5>Tabla</h5>
            <input class="m-1" type="radio" v-model="verTabla" :value="true">Mostrar 
            <input class="m-1" type="radio" v-model="verTabla" :value="false">Ocultar 

        </div>  
        <div v-if="verTabla== true">

        <p class="bg-light p-2 m-3">Ingresá los valores solicitados (bootstrap)
         </p>
        <div class="m-3">
            <label for="exampleFormControlInput1" class="form-label">Encabezado: Background-color</label>
            <input type="text" class="form-control"  v-model="colorTablaForm" 
            id="exampleFormControlInput1" placeholder="Ejemplo: bg-success">
        </div>

        <div class="m-3">
            <label for="exampleFormControlInput1" class="form-label">Texto: Text-color</label>
            <input type="text" class="form-control"  v-model="colorTablaFuente" 
            id="exampleFormControlInput1" placeholder="Ejemplo: text-white">
        </div>
        <section class="w-50 mx-4">        
            <h4 class="m-1">Tabla con datos</h4>
                <Tabla :tareasTabla="tareasForm" :bgColorTablaSecondary="bgColorTablaSecondaryForm"
                :bgColorTablaSuccess="bgColorTablaSuccessForm" :bgColor="bgColorForm" 
                :colorTabla="colorTablaForm" :fontColorTabla="colorTablaFuente" />
             
                <div v-if="mostrarMsgDelHijo" :class="msgPink" class="p-1"> {{mensajePadre}}</div>
                <div class="bg-light m-4 p-2">
                    <h6 class="px-3 m-2">Agregar una nueva tarea</h6>
                        <input type="text" class="m-3 w-75 form-control" v-model="nuevaTarea"
                        @keyup.enter="agregarTarea" >
                         <!-- @keydown="eventoTeclado" -->
                        <button type="button" class="btn btn-primary mx-3" @click="agregarTarea">
                            Confirmar
                        </button>
                </div>
        </section>
        <div class="w-50 m-4">      
  
            <div v-if="verMas" class="m-5">
                    <VerMas :cardVerMas="verMas" :data-toggle="modal" 
                    />     
            </div>      
             
        </div>
    </div>
      <!-- The Modal -->
      <div v-show="userCreate">
         <modalVacio  @mensajeHijo="mensajePadre = $event" >
          </modalVacio>  
    </div>

  </div>
</template>
<script>
import Tabla from './Tabla.vue';
import VerMas from './VerMas.vue';
import ModalVacio from './ModalVacio.vue'
export default {  
    name: 'Formulario',  
    components:{
        Tabla,
        VerMas,
        ModalVacio,
    },
    data: () => ({
            nombreForm: '',
            emailForm: '',
            textareaForm:'',
            bgColorForm:'bg-warning',
            bgColorTablaSecondaryForm:'bg-secondary',
            bgColorTablaSuccessForm:'bg-success',
            colorTablaForm:'',
            nuevaTarea:'',
            colorTablaFuente:'',
            verTabla: true,
            verMas: true,
            modal:'modal',
            azul:'#3a72aa',
            alert:false,
            mensajePadre:'',
            msgPink:'msgPink',  
            mostrarMsgDelHijo: false, 
            teclaPresionada: false,
            userCreate:false,
        
            tareasForm:[
                { id:1, descripcion: "Realizar tarea 1"},
                { id:2, descripcion: "Realizar tarea 2"},
                { id:3, descripcion: "Realizar tarea 3"},
                { id:4, descripcion: "Realizar tarea 4"},      
            ]
    }),
     methods:{
        agregarTarea(){
            if(this.nuevaTarea !== ''){
                this.tareasForm.push({
                    id: 5,
                    descripcion:this.nuevaTarea,      
                    });
                    this.nuevaTarea='',
                    this.mostrarMsgDelHijo = false
                }else{      
                    this.mostrarMsgDelHijo = true 
                    this.userCreate = true
                }
    },
     
  
    },

  }
</script>
