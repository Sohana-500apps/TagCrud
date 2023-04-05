<template>
    <!-- Modal component starts here -->
    <div id="popup-modal" tabindex="-1" class="fixed top-0 left-0 right-0 z-50  p-4 overflow-x-hidden overflow-y-auto md:inset-0 h-[calc(100%-1rem)] md:h-full">
        <div class="relative w-full h-full max-w-md md:h-auto">
            <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
                <!-- closing the model when I click on cross icon -->
                <button type="button" class="absolute top-3 right-2.5 text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center dark:hover:bg-gray-800 dark:hover:text-white" @click="closeTagModel">
                    <svg aria-hidden="true" class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
                    <span class="sr-only">Close modal</span>
                </button>
                <div class="p-6 text-center">
                   <!-- Adding the tagname starts here -->
                    <form class=" px-8 pt-6 pb-8">
                        <div class="mb-4">
                          <label class="block text-gray-700 text-sm font-bold mb-2" for="name">
                            TagName
                          </label>
                          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="tag" type="text" placeholder="Enter Tag" v-model="name" required>
                        </div>
                        </form>
                        <!-- Save and cancel button starts here   -->
                    <button data-modal-hide="popup-modal" type="button" class="text-white bg-red-600 hover:bg-red-800 focus:ring-4 focus:outline-none focus:ring-red-300 dark:focus:ring-red-800 font-medium rounded-lg text-sm inline-flex items-center px-5 py-2.5 text-center mr-2" @click="save">
                        Save
                    </button>
                    <button data-modal-hide="popup-modal" type="button" class="text-gray-500 bg-white hover:bg-gray-100 focus:ring-4 focus:outline-none focus:ring-gray-200 rounded-lg border border-gray-200 text-sm font-medium px-5 py-2.5 hover:text-gray-900 focus:z-10 dark:bg-gray-700 dark:text-gray-300 dark:border-gray-500 dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-gray-600" @click="closeTagModel">Cancel</button>
                  <!-- Save and cancel button ends here   -->
                </div>
                <!-- Adding the tagname ends here -->
            </div>
        </div>
    </div>
    <!-- Modal component ends here -->
</template>
<script setup lang="ts">

const name=ref("")
//Defining the schema of TagUrl
interface TagUrl{
    url:string
}
// Getting the props of url
let props = defineProps<{ url:TagUrl }>()
// Emitting the close 
const emits = defineEmits(['close-modal']);
const closeTagModel=()=>{
    emits('close-modal')
}
//Saving the data
const save=()=>{
  useAuthLazyFetchPost(`${props.url}/`, {
    body: {
      project_id: '123',
      name: name.value,
      entity: 'CONTACTS',
    }
  });
}

</script>