<template>
  <div>
     <!--Start of  tag-->
        <div class="p-[50px] flex divide-y-2 border-y">
           
            <h1>Tags</h1>
             <!--Registering of  add tag start-->
            <CollectionTagsAdd  :url="url"/>
             <!--Registering of  add tag end-->
        </div>
        <div class="text-center">
             <!--Registering of  taglist start-->
        <CollectionTagsList :tagurl="tagurl" :url="url"/>
        <!--Registering of  taglist end-->
      </div>
      </div>
       <!--End of  tag-->
</template>
<script setup lang="ts">
//importing the heroIcon and useAuthLazyFetch

import { PlusIcon } from "@heroicons/vue/24/outline"
import {useAuthLazyFetch}  from "../../../composables/useAuthLazyFetch"

//Desscribing the schema of tagurl and url
interface TagUrl{
    tagurl:string,
    url:string
}
// Get the props of tagurl and url
const props = withDefaults(defineProps<TagUrl>(), {
    tagurl: "",
    url:""
})



</script>