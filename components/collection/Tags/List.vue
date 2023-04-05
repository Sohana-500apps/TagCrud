<template>
    <div>
        <!-- start of showing dynamic tag -->
    <h1 class="text-3xl">Tag List</h1>
    <div class="flex flex-wrap">
        <!-- Click the edit model that textbox should be open -->
      <div v-for="(tag,index) in tagurldata" :key="tag" class="max-w-[7rem] mr-10 rounded  shadow-lg flex">
        <div>
            <textarea v-if="editIndex===index" v-model="editname" class="w-[8rem] h-[3rem]"></textarea>
        <h1 v-else>{{tag.name}}</h1> 
       </div> 
       <!-- Registering the delete tag start here -->
         <CollectionTagsDelete @delete="deletetag(tag.uid)"/>
          <!-- Registering the delete tag ends here -->
          <!-- Edit starts here -->
         <button @click="edittag(index,tag.uid,tag.project_id,tag.entity)">      
          <PencilIcon class="h-6 w-6"/>
         </button>
         <!-- Edit ends here -->
      </div>
    </div>
     <!-- end of showing dynamic tag -->
</div>
</template>
<script setup lang="ts">
//Importing the useAuthLazyfetch and HeroIcon
import {useAuthLazyFetch}  from "../../../composables/useAuthLazyFetch"
import { PencilIcon } from "@heroicons/vue/24/outline"

//Descrinong the schema of tagurl and url
interface TagUrl{
    tagurl:string,
    url:string
}
// Get props of tagUel and url
const props = withDefaults(defineProps<TagUrl>(), {
    tagurl: "",
    url:""
})
// Assigning the  number value to editINDEX
const editIndex=ref("0")
const editname=ref("")

//Showing the dynamic tag in the list
const gettagurl = async () => {
    try {
    const { data: tagurldata } = await useAuthLazyFetch(props.tagurl, {});
    console.log("urldata", tagurldata); // Log the urldata
    return tagurldata;
  } catch (error) {
    console.error("Error fetching tag URL", error);
    return null;
  }
}
const tagurldata = await gettagurl();

// Deleting the tag when I click on any tag
const deletetag=(uid:any)=>{
    console.log('I am deleting',uid)
    useAuthLazyFetchDelete(`${props.url}/${uid}`, {});
    let tagurlIndex=tagurldata.value.findIndex(tag => tag.uid === uid)
    if(tagurlIndex!==-1){
        tagurldata.value.splice(tagurlIndex,1)
    }
}
//Edit the tag  when I click on any tag
const edittag=(index,uid,projectid,entity)=>{
    editIndex.value=index
   
    useAuthLazyFetchPut(`${props.url}/${uid}?name=${editname.value}`, {
    body: {
      project_id: projectid,
      name: editname.value,
      entity: entity,
    },
  });
}
</script>