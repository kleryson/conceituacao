<script setup lang="ts">
import { UserIcon } from 'vue-tabler-icons'
const token = useCookie('token')
const user = useCookie('user')

const logout = () => {
  token.value = null
  user.value = null
  navigateTo('/auth/login')
}

</script>

<template>
    <v-menu :close-on-content-click="false">
        <template v-slot:activator="{ props }">
            <v-btn class="profileBtn custom-hover-primary" variant="text" v-bind="props" icon>
                <v-avatar size="35">
                    <img src="/images/users/avatar-1.jpg" height="35" alt="user" />
                </v-avatar>
            </v-btn>
        </template>
        <v-sheet rounded="md" width="200" elevation="10" class="mt-2">
            <v-list class="py-0" lines="one" density="compact">
                <v-list-item value="item1" active-color="primary" >
                    <template v-slot:prepend>
                        <UserIcon stroke-width="1.5" size="20"/>
                    </template>
                    <v-list-item-title class="pl-4 text-body-1">Meu Perfil</v-list-item-title>
                </v-list-item>
            </v-list>
            <div class="pt-4 pb-4 px-5 text-center">
                <v-btn  color="primary" variant="outlined" block @click="logout">Logout</v-btn>
            </div>
        </v-sheet>
    </v-menu>
</template>
