<script setup>
import { ref } from 'vue'
import {useAuth } from '@/composables/useAuth'

const { isAuthenticated, logout, user } = useAuth()
const brand = ref('🏦 Fake Company Directory')   
</script>

<template>

<nav>
    <div class="wrapper">
      <RouterLink :to="{ name: 'Home' }" class="brand">
        <span class="brand-title">{{ brand }}</span>
      </RouterLink>
      <div class="menu">
        <p v-show="isAuthenticated" class="px-2 py-4">
          Welcome back
          <strong>
            <i>{{ user.email }}</i>
          </strong>
        </p>
        <div v-if="isAuthenticated">
          <RouterLink :to="{ name: 'Settings' }" href="#" class="menu-item">Settings</RouterLink>
          <button class="menu-logout" @click="logout">Logout</button>
        </div>
        <div v-else>
          <RouterLink :to="{ name: 'Login' }" href="#" class="menu-login">Login</RouterLink>
        </div>
      </div>
    </div>
  </nav>
    

</template>

<style scoped lang="postcss"> 
    nav {
        @apply flex h-20 bg-blue-900 text-slate-200;
        .wrapper {
            @apply container mx-auto flex w-full items-center justify-between;
            .brand { 
                 
               &-title {
                
                    @apply text-2xl font-bold text-slate-300;
               }
            }

            .menu {
                    @apply flex gap-2;
                    & div {
                        @apply py-2;
                      }
              
                    &-item {
                        @apply rounded-md px-4 py-2 hover:bg-slate-900 hover:text-slate-100;
                    }
                    &-login {
                        @apply rounded-md bg-green-500 px-4 py-2 text-red-100 hover:bg-green-700;
                    }
                    &-logout {
                        @apply mx-2 rounded-md bg-red-500 px-4 py-2 text-red-100 hover:bg-red-700;
                      }
            }

        }
    }
</style>