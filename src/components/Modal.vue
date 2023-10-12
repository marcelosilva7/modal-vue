<template>
    <div class="modal">
        <div class="modal-dentro">
            <slot />
            <!-- usando a função para trocar o estado do modal-->
            <button class="modal-fechar" @click="toggleModal()">Fechar o modal</button>
        </div>
    </div>
</template>

<script setup lang="ts">

import { ref } from 'vue';
//aqui importando a função para ser usada no modal
const props = defineProps({
    toggleModal: {
        type: Function,
        required: true,
    },
});
//outra parte do import
const { toggleModal } = props;

</script>


<style scoped>
.modal{
    position: fixed;
    top:0;
    left:0;
    right:0;
    bottom: 0;
    z-index: 99;
    background-color: rgb(0, 0, 0, 0.2);

    display: flex;
    align-items: center;
    justify-content: center; 
    
}

.modal-dentro{
        background: #FFF;
        padding: 32px;
    }  


</style>