<template>
    <div>
        <!-- Start of TagMain  -->
    <CollectionTagsMain :url="url" :tagurl="tagurl"/>
    <!-- End of TagMain  -->
</div>
</template>
<script setup lang="ts">
const url="https://v1-orm-lib.mars.hipso.cc/tags"
const tagurl="https://v1-orm-lib.mars.hipso.cc/tags/entity/CONTACTS?offset=0&limit=100&sort_column=id&sort_direction=desc"
</script>