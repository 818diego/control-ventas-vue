<template>
  <v-app>
    <v-app-bar app color="black">
      <v-btn icon @click="toggleDrawer" class="mr-4">
        <v-icon class="white--text">mdi-menu</v-icon>
      </v-btn>
      <v-toolbar-title>
        <span class="white--text" style="font-size: 20px;">Sistema de ventas</span>
      </v-toolbar-title>
      <v-btn icon class="ml-auto">
        <v-icon class="white--text">mdi-account-circle</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon class="white--text">mdi-magnify</v-icon>
      </v-btn>
    </v-app-bar>

    <!-- Menú lateral (navigation drawer) -->
    <v-navigation-drawer app v-model="drawer">
      <v-list dense>
        <v-list-item to="/home" @click="closeDrawerAndNavigateTo('home')">
          <v-list-item-action>
            <v-icon>mdi-home</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Inicio</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-divider></v-divider>


        <template>
          <v-list-group>
            <v-list-item slot="activator">
              <v-list-item-content>
                <v-list-item-title>
                  Almacén
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>

            <v-list-item :to="{ name: 'categorias' }">
              <v-list-item-action>
                <v-icon class="mdi mdi-shape-plus"></v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Gestión de categorías
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>

            <v-list-item :to="{ name: 'articulos' }">
              <v-list-item-action>
                <v-icon class="mdi mdi-database"></v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Gestión de artículos
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>

          </v-list-group>
        </template>
        <v-divider></v-divider>



        <template>
          <v-list-group>
            <v-list-item slot="activator">
              <v-list-item-content>
                <v-list-item-title>
                  Usuarios
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>

            <v-list-item :to="{ name: 'roles' }">
              <v-list-item-action>
                <v-icon class="mdi mdi-account-multiple-plus-outline"></v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Gestión de roles
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>

            <v-list-item :to="{ name: 'usuarios' }">
              <v-list-item-action>
                <v-icon class="mdi mdi-account"></v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Gestión de usuarios
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </template>
        <v-divider></v-divider>

        <template>
          <v-list-group>
            <v-list-item slot="activator">
              <v-list-item-content>
                <v-list-item-title>
                  Ventas
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>

            <v-list-item :to="{ name: 'ventas' }">
              <v-list-item-action>
                <v-icon class="mdi mdi-cash-multiple"></v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Ventas
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>

            <v-list-item :to="{ name: 'clientes' }">
              <v-list-item-action>
                <v-icon class="mdi mdi-account-switch"></v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Gestión de clientes
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </template>
        <v-divider></v-divider>

        <!--COMPRAS -->
        <template>
          <v-list-group>
            <v-list-item slot="activator">
              <v-list-item-content>
                <v-list-item-title>
                  Compras
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>

            <v-list-item :to="{ name: 'ingresos' }">
              <v-list-item-action>
                <v-icon class="mdi mdi-currency-usd"></v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Ingresos
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>

            <v-list-item :to="{ name: 'proveedor' }">
              <v-list-item-action>
                <v-icon class="mdi mdi-account-group"></v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Gestión de proveedores
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </template>
        <v-divider></v-divider>

        <!--CONSULTAS -->
        <template>
          <v-list-group>
            <v-list-item slot="activator">
              <v-list-item-content>
                <v-list-item-title>
                  Consultas
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>

            <v-list-item :to="{ name: 'consultarVentas' }">
              <v-list-item-action>
                <v-icon class=" mdi mdi-book-multiple"></v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Consultar ventas
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>

            <v-list-item :to="{ name: 'consultarCompras' }">
              <v-list-item-action>
                <v-icon class=" mdi mdi-book-multiple">t</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Consultar compras
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </template>
        <v-divider></v-divider>

        <template>
          <v-list-group>
            <v-list-item slot="activator">
              <v-list-item-content>
                <v-list-item-title>
                  Graficas
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>

            <v-list-item :to="{ name: 'graficasVentas' }">
              <v-list-item-action>
                <v-icon>query_stats</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Graficas ventas
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>

            <v-list-item :to="{ name: 'graficasIngresos' }">
              <v-list-item-action>
                <v-icon>query_stats</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  Graficas compras
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </template>
        <v-divider></v-divider>

        <!-- Botón para mostrar la modal -->
        <v-list-item>
          <v-list-item-action>
            <v-btn @click="showModal" text color="red">Agradecimientos</v-btn>
          </v-list-item-action>
        </v-list-item>
        <!-- Modal -->
        <v-dialog v-model="modal" persistent max-width="400">
          <v-card>
            <v-card-title class="headline">Nose que poner aqui 😂</v-card-title>
            <v-card-text>
              Sistema Hecho por el grupo de ISyTE 1ra generación, en conjunto con el profesor 
              Victor, para la materia de Ingenieria de Software y Tecnologias Emergentes, durante 
              6to semestre de la carrera, Gracias.
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="primary" @click="modal = false">Cerrar</v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-list>
    </v-navigation-drawer>

    <v-content>
      <h1 class="text-center success--text mt-10">Zona de trabajo pa</h1>
      <router-view />
    </v-content>
    <v-footer>
      <v-card height="30" width="100%" class="text-center white--text" color="black lighten-4">
        <h3> ISyTE - FIAD-UABC - {{ new Date().getFullYear() }} </h3>
      </v-card>
    </v-footer>
  </v-app>
</template>


<script>
export default {
  data() {
    return {
      drawer: false,
      modal: false,
    };
  },
  methods: {
    toggleDrawer() {
      this.drawer = !this.drawer;
    },
    closeDrawerAndNavigateTo(routeName) {
      this.drawer = false;
      this.$router.push({ name: routeName });
    },
    showModal() {
      this.modal = true;
    },
  },
};
</script>
