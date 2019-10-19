<template>
   <v-layout align-start>
       <v-flex>
            <v-data-table
                    :headers="headers"
                    :items="categorias"
                    :search="search"
                    sort-by="nombre"
                    class="elevation-1"
                    >
                <template v-slot:item.action="{ item }">
                        <v-icon
                        small
                        class="mr-2"
                        @click="editItem(item)"
                        >
                        edit
                        </v-icon>
                        <v-icon
                        small
                        @click="deleteItem(item)"
                        >
                        delete
                        </v-icon>
                    </template>
                        <template v-slot:top>
                            <v-toolbar flat color="white">
                            <v-toolbar-title>Categorias</v-toolbar-title>
                            <v-divider
                                class="mx-4"
                                inset
                                vertical
                            ></v-divider>
                            <v-spacer></v-spacer>
                            <v-dialog v-model="dialog" max-width="500px">
                                <template v-slot:activator="{ on }">
                                <v-btn color="primary" dark class="mb-2" v-on="on">Nuevo</v-btn>
                                </template>
                                <v-card>
                                <v-card-title>
                                    <span class="headline">{{ formTitle }}</span>
                                </v-card-title>
                    
                                <v-card-text>
                                    <v-container>
                                    <v-row>
                                        <v-col cols="12" sm="6" md="4">
                                        <v-text-field v-model="nombre" label="Nombre"></v-text-field>
                                        </v-col>
                                        <v-col cols="12" sm="6" md="4">
                                        <v-text-field v-model="descripcion" label="Descipcion"></v-text-field>
                                        </v-col>


                                         <v-col cols="12" sm="6" md="4" v-show="valida">
                                       <div class="red--text" v-for="v in validaMensaje" :key="v" v-text="v">    </div>
                                        </v-col>
                                        
                                    </v-row>
                                    </v-container>
                                </v-card-text>
                    
                                <v-card-actions>
                                    <v-spacer></v-spacer>
                                    <v-btn color="blue darken-1" text @click="close">Cancelar</v-btn>
                                    <v-btn color="blue darken-1" text @click="guardar">Guardar</v-btn>
                                </v-card-actions>
                                </v-card>
                            </v-dialog>
                            </v-toolbar>
                        </template>

               
                <template v-slot:no-data>
                        <v-btn color="primary" @click="initialize">Reset</v-btn>
                </template>
            </v-data-table>
       </v-flex>
   </v-layout>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return {
            categorias:[],
                search:'',
                dialog: false,
                    headers: [
                    { text: 'Opciones', value: 'opciones', sortable: false },
                    { text: 'Nombre', value: 'nombre' },
                    { text: 'Descripcion', value: 'descripcion', sortable:false },
                    { text: 'Estado', value: 'condicion', sortable:false },
                    ],
                   
                    editedIndex: -1,

                    editedItem: {
                        name: '',
                        calories: 0,
                        fat: 0,
                        carbs: 0,
                        protein: 0,
                    },
                    id:'',
                    nombre:'',
                    descripcion:'',
                    valida:0,
                    validaMensaje:[]
                    
        }
    },
    computed: {
        formTitle () {
        return this.editedIndex === -1 ? 'Nueva categoria' : 'Actualizar categoria'
        },
    },

    watch: {
        dialog (val) {
        val || this.close()
        },
    },

    created () {

        this.listar();
    },

    methods:{
        listar(){
            let me = this;
            axios.get('api/Categorias/Listar').then(function(response){
                //console.table(response.data);
                me.categorias = response.data;
            })  .catch(function(error){
console.log(error);
            });
        },
       

                editItem (item) {
                this.editedIndex = this.desserts.indexOf(item)
                this.editedItem = Object.assign({}, item)
                this.dialog = true
                },

                deleteItem (item) {
                const index = this.desserts.indexOf(item)
                confirm('Are you sure you want to delete this item?') && this.desserts.splice(index, 1)
                },

                close () {
                this.dialog = false
                
                },

                limpiar(){
                this.id="";
                this.nombre = "";
                this.descripcion="";
                },

                guardar () {
                    if(this.validar()){
                        return;
                    }  
                    if (this.editedIndex > -1) {
                        //Codigo para editar
                    } else {
                        //Codigo para guardar
                        let me = this;
                        axios.post('api/Categorias/Crear',{'nombre':me.nombre, 'descripcion':me.descripcion}).then(function(response){
                             me.close();
                            me.listar();
                            me.limpiar();
                           
                        }).catch(function(error){
                            console.log(error);
                        });
                    }                    
                },

                validar(){
                    this.valida = 0;
                    this.validaMensaje=[];
                    if(this.nombre.length<3|| this.nombre.length>50){
                            this.validaMensaje.push("Nombre debe tener mas de 3 caracteres y menos de 50");
                    }
                    if(this.validaMensaje.length){
                        this.valida = 1;
                    }  
                    return this.valida;
                }
    }
}
</script>