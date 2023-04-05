<template>
    <!-- Register of Tag  start here-->
    <CollectionTagsTag :tagurl="tagurl" :url="url"/>
     <!-- Register of Tag  ends here-->
</template>
<script setup lang="ts">
//Describing the schema of tagurl
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