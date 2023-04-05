<template>
    <div>
        <!-- start of Delete tag -->
        <button id="deletetag" @click="emitdelete">
            <TrashIcon class="h-6 w-6"/>
        </button>
         <!-- End of Delete tag -->
    </div>
</template>
<script setup lang="ts">
//importimng tje heroicon
import { TrashIcon } from "@heroicons/vue/24/outline"

//Emitting the delete
const emits = defineEmits(['delete']);
const  emitdelete=()=>{
emits('delete')
}
</script>