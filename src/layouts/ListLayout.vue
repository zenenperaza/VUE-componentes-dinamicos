<template>
    <div> 
        <h1>Componente List</h1>
        <div class="container">
            <UserList v-for="item in props.content" :key="item.name" :content="item" />
        </div>
    </div>
    </template>
    
    <script lang="ts" setup>
       import { defineProps } from 'vue'
       import UserList from '@/components/UserList.vue';
    
       const props = defineProps(['content'])
    </script>
    
    <style scoped>
    .container{
        width: 100%;
        display: flex;
        justify-content: flex-start;
        align-items: flex-start;
        flex-wrap: wrap;
    }
    </style>