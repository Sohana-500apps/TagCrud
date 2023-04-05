<template>
    <div>
       <!-- start of Add tag  -->
    <div class="ml-[56rem]">
        <button class="flex bg-slate-100" @click="openTagModal">
        <PlusIcon class="h-6 w-6"/>
        <p class="ml-3">Add Tag</p>
        </button>
    </div>
    <CollectionTagsAddModal v-show="isTagModel" @close-modal="isTagModel=false"  :url="url"/>
     <!-- End of Add tag  -->
</div>
</template>
<script setup lang="ts">
//importing the heroIcon
import { PlusIcon } from "@heroicons/vue/24/outline"
import {ref} from 'vue'
const isTagModel=ref(false)
//opening the model
const openTagModal=()=>{
    isTagModel.value=!isTagModel.value
}
//Defining the schema of url
interface TagUrl{
    url:string
}
// Getting props of  url
const props = defineProps<{ url:TagUrl }>()

</script>