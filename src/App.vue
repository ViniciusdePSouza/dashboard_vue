<template>
  <v-app theme="dark">
    <v-navigation-drawer v-model="isDrawerOpen">
      <v-list>
        <v-list-subheader>Menu</v-list-subheader>
        <v-list-item prepend-icon="mdi-home">Home</v-list-item>
        <v-list-item prepend-icon="mdi-account">Usuários</v-list-item>

        <v-list-group value="Clientes">
          <template v-slot:activator="{ props }">
            <v-list-item v-bind="props" prepend-icon="mdi-account-circle"
              >Clientes</v-list-item
            >
          </template>

          <v-list-item prepend-icon="mdi-currency-usd">Vendas</v-list-item>
          <v-list-item prepend-icon="mdi-chart-line">Relatório</v-list-item>
        </v-list-group>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar flat class="border-b">
      <v-app-bar-nav-icon
        @click="isDrawerOpen = !isDrawerOpen"
      ></v-app-bar-nav-icon>
      <v-app-bar-title>Meu app</v-app-bar-title>

      <template #append>
        <v-menu>
          <template #activator="{ props }">
            <v-btn icon class="mr-2" v-bind="props">
              <v-badge dot>
                <v-icon icon="mdi-bell-outline"></v-icon>
              </v-badge>
            </v-btn>
          </template>

          <v-card min-width="300px">
            <v-list nav density="compact">
              <v-list-item prepend-icon="mdi-message-alert">
                <v-list-item-title>
                  Require password for purchase or use password to restrict
                  purchase
                </v-list-item-title>
              </v-list-item>
              <v-list-item prepend-icon="mdi-message-alert">
                <v-list-item-title>
                  Require password for purchase or use password to restrict
                  purchase
                </v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card>
        </v-menu>

        <v-menu>
          <template #activator="{ props }">
            <v-avatar v-bind="props">
              <v-img src="http://github.com/ViniciusdePSouza.png" cover />
            </v-avatar>
          </template>

          <v-card min-width="200px">
            <v-list nav density="compact">
              <v-list-item prepend-icon="mdi-account-outline">
                <v-list-item-title>Meu perfil</v-list-item-title>
              </v-list-item>
              <v-list-item prepend-icon="mdi-heart-outline">
                <v-list-item-title>Favoritos</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card>
        </v-menu>
      </template>
    </v-app-bar>

    <v-main>
      <v-container>
        <h1>Dashborad</h1>

        <v-card flat class="border mb-4">
          <div class="d-flex justify-space-between align-items-center">
            <v-card-title>Últimos Usuários</v-card-title>

            <v-card-title>
              <v-btn
                @click="isDialogOpen = !isDialogOpen"
                icon="mdi-plus"
                variant="tonal"
                size="small"
              />

              <v-dialog width="600px" v-model="isDialogOpen">
                <v-card>
                  <v-card-title>Adicionar Usuário</v-card-title>
                  <v-card-text>
                    <v-row>
                      <v-col>
                        <v-text-field
                          label="Nome"
                          variant="outlined"
                          :rules="nameRules"
                        />
                      </v-col>
                      <v-col>
                        <v-text-field
                          label="Email"
                          variant="outlined"
                          :rules="emailRules"
                        />
                      </v-col>
                    </v-row>

                    <v-select
                      label="Cargo"
                      variant="outlined"
                      :items="['Admin', 'Gerente', 'Convidado']"
                      :rules="selectRules"
                    />
                  </v-card-text>

                  <v-card-actions>
                    <v-spacer />
                    <v-btn variant="tonal" color="success">Salvar</v-btn>
                    <v-btn
                      variant="tonal"
                      color="text"
                      @click="isDialogOpen = false"
                      >Cancelar</v-btn
                    >
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </v-card-title>
          </div>
          <v-table>
            <thead>
              <tr>
                <th>Nome</th>
                <th>Email</th>
                <th>Cargo</th>
                <th></th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="user in allUsers" :key="user.id">
                <td>{{ user.name }}</td>
                <td>{{ user.email }}</td>
                <td>
                  <v-chip color="primary" variant="outlined" size="small">
                    {{ user.role }}
                  </v-chip>
                </td>
                <td class="border-top">
                  <v-btn variant="tonal" color="primary"> Editar </v-btn>
                </td>
              </tr>
            </tbody>
          </v-table>
        </v-card>

        <v-row>
          <v-col cols="12" md="4" lg="3" sm="6">
            <v-card flat class="border">
              <v-img
                src="https://images.pexels.com/photos/427679/pexels-photo-427679.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                cover
                class="align-end text-white"
              >
                <v-card-title>
                  Top 10 lugares para se visitar em londres
                </v-card-title>
              </v-img>
              <v-card-subtitle class="pt-3 font-weight-medium">
                Reino unido
              </v-card-subtitle>

              <v-card-text>
                <div>Big Bang</div>

                <div>Lorem Ipsum is simply dummy text of the printing and</div>
              </v-card-text>

              <v-card-actions>
                <v-btn
                  class="font-weight-bold"
                  color="primary"
                  variant="outlined"
                  >Ver mais</v-btn
                >
                <v-btn
                  prepend-icon="mdi-cart"
                  class="font-weight-bold"
                  color="primary"
                  variant="warning"
                  >Comprar</v-btn
                >
              </v-card-actions>
            </v-card>
          </v-col>
          <v-col cols="12" md="4" lg="3" sm="6">
            <v-card flat class="border">
              <v-img
                src="https://images.pexels.com/photos/427679/pexels-photo-427679.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                cover
                class="align-end text-white"
              >
                <v-card-title>
                  Top 10 lugares para se visitar em londres
                </v-card-title>
              </v-img>
              <v-card-subtitle class="pt-3 font-weight-medium">
                Reino unido
              </v-card-subtitle>

              <v-card-text>
                <div>Big Bang</div>

                <div>Lorem Ipsum is simply dummy text of the printing and</div>
              </v-card-text>

              <v-card-actions>
                <v-btn
                  class="font-weight-bold"
                  color="primary"
                  variant="outlined"
                  >Ver mais</v-btn
                >
                <v-btn
                  prepend-icon="mdi-cart"
                  class="font-weight-bold"
                  color="primary"
                  variant="warning"
                  >Comprar</v-btn
                >
              </v-card-actions>
            </v-card>
          </v-col>
          <v-col cols="12" md="4" lg="3" sm="6">
            <v-card flat class="border">
              <v-img
                src="https://images.pexels.com/photos/427679/pexels-photo-427679.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                cover
                class="align-end text-white"
              >
                <v-card-title>
                  Top 10 lugares para se visitar em londres
                </v-card-title>
              </v-img>
              <v-card-subtitle class="pt-3 font-weight-medium">
                Reino unido
              </v-card-subtitle>

              <v-card-text>
                <div>Big Bang</div>

                <div>Lorem Ipsum is simply dummy text of the printing and</div>
              </v-card-text>

              <v-card-actions>
                <v-btn
                  class="font-weight-bold"
                  color="primary"
                  variant="outlined"
                  >Ver mais</v-btn
                >
                <v-btn
                  prepend-icon="mdi-cart"
                  class="font-weight-bold"
                  color="primary"
                  variant="warning"
                  >Comprar</v-btn
                >
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref, onMounted } from "vue";
import { api } from "@/services/api.js";

const allUsers = ref([]);
const isDrawerOpen = ref(false);
const groupValue = ref(false);
const isDialogOpen = ref(false);

const emailRules = [
  (value) => {
    if (value) return true;

    return "Email obrigatório";
  },
];

const nameRules = [
  (value) => {
    if (value) return true;

    return "Nome obrigatório";
  },
];

const selectRules = [
  (value) => {
    if (value) return true;

    return "Selecione um cargo";
  },
];

onMounted(async () => {
  try {
    const { data } = await api.get("/users");

    allUsers.value = data;
  } catch (e) {
    console.log(e);
  }
});
</script>

<style></style>
