<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      :clipped="$vuetify.breakpoint.lgAndUp"
      app
    >
      <v-list dense>

        <template>
          <v-list-item :to="{name:'home'}">
              <v-list-item-action>
                  <v-icon>home</v-icon>
              </v-list-item-action>
              <v-list-item-title>
              Inicio
              </v-list-item-title>
          </v-list-item>          
         </template>

        <template>
          <v-list-group>
            <template v-slot:activator>
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title>
                    Almacen
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </template>

            <v-list-item :to="{name:'categorias'}">
                <v-list-item-action>
                  <v-icon>table_chart</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title>
                        Categorias
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item>

             <v-list-item>
                <v-list-item-action>
                  <v-icon>table_chart</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title>
                        Articulos
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item>
          </v-list-group>
          </template> 


        <template>
          <v-list-group>
            <template v-slot:activator>
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title>
                    Compras
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </template>

            <v-list-item>
                <v-list-item-action>
                  <v-icon>table_chart</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title>
                        Ingresos
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item>

             <v-list-item>
                <v-list-item-action>
                  <v-icon>table_chart</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title>
                        Proveedores
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item>
          </v-list-group>
          </template> 

          
        <template>
          <v-list-group>
            <template v-slot:activator>
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title>
                    Ventas
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </template>

            <v-list-item>
                <v-list-item-action>
                  <v-icon>table_chart</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title>
                        Ventas
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item>

             <v-list-item>
                <v-list-item-action>
                  <v-icon>table_chart</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title>
                        Clientes
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item>
          </v-list-group>
          </template> 

          
        <template>
          <v-list-group>
            <template v-slot:activator>
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title>
                    Accesos
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </template>

            <v-list-item>
                <v-list-item-action>
                  <v-icon>table_chart</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title>
                        Roles
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item>

             <v-list-item>
                <v-list-item-action>
                  <v-icon>table_chart</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title>
                        Usuarios
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item>
          </v-list-group>
          </template> 
  
  <template>
          <v-list-group>
            <template v-slot:activator>
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title>
                    Consultas
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </template>

            <v-list-item>
                <v-list-item-action>
                  <v-icon>table_chart</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title>
                        Consultas compras
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item>

             <v-list-item>
                <v-list-item-action>
                  <v-icon>table_chart</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title>
                        Consultas ventas
                    </v-list-item-title>
                </v-list-item-content>
            </v-list-item>
          </v-list-group>
          </template> 

      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      :clipped-left="$vuetify.breakpoint.lgAndUp"
      app
      color="blue darken-3"
      dark
    >
      <v-toolbar-title
        style="width: 300px"
        class="ml-0 pl-4"
      >
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <span class="hidden-sm-and-down">Sistema</span>
      </v-toolbar-title>

      <v-spacer></v-spacer>
      <v-btn icon>
        <v-icon>apps</v-icon>
      </v-btn>
      
    </v-app-bar>
    <v-content>
      <v-container
        class="fill-height"
        fluid
      >
      <v-slide-y-transition mode="out-in">
          <router-view/>
      </v-slide-y-transition>
      </v-container>
    </v-content>
  <v-footer>
    <v-spacer></v-spacer>
    <div>Jhonnatan Flores&copy;2019 </div>
  </v-footer>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
  data: () => ({
    //
          drawer: null,

  }),
};
</script>
