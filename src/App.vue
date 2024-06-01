  
<script setup>
import {ref} from 'vue'
import { onClickOutside } from '@vueuse/core';

const isModalOpen = ref(false)
const modal = ref(null)

onClickOutside(modal, ()=>(isModalOpen.value = false))
  
</script>

<template>
  <div class="">
    <h2 class="text-center my-5 text-green-500 text-xl font-semibold">Vue 3 Modall !</h2>
    <button @click="isModalOpen = true" class="bg-green-100 text-green-600 font-medium m-auto block px-4 py-2"> Open modile </button>
    <Teleport to="body">
      <Transition name="modal">
        <div v-if="isModalOpen" class="fixed top-0 left-0 w-full h-full bg-green-50 bg-opacity-50 flex justify-center items-center">
          <div class="modal m-auto" ref="modal">
            <button @click="isModalOpen = false " class="bg-green-300 float-right mt-2 py-0.5 px-4 text-black font-normal text-lg me-4 ">
                close
            </button>
            <div class="absolute top-[50%] translate-y-[-50%] w-full block text-center text-green-600">
              Click outside this modal to close it
            </div>
          </div>
        </div>
      </Transition>
    </Teleport>
  </div>
</template>

<style scoped>

.modal-enter-active,
.modal-leave-active {
  transition: all 0.4s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
  transform: scale(1.1);
  /* transform:scale(0.9) */

}


.modal {
  position: fixed;
  z-index: 999;
  top: 30%;
  width: 300px;
  height: 200px;
  background: rgb(203, 244, 203);
}
</style>

