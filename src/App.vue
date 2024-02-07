<script setup>
import { reactive } from 'vue'
import Modal from './components/Modal.vue'

const state = reactive({ isVisibleModal: false })
const onOpenModal = () => state.isVisibleModal = true
const onCloseModal = () => state.isVisibleModal = false
</script>

<template>
  <button @click="onOpenModal">Open Modal</button>
  <Modal v-model="state.isVisibleModal">
    <template #header>
      Modal Title
    </template>
    <template #content>
      <p>
        Modal content Lorem ipsum dolor sit amet, consectetur adipisicing elit. Odit, amet iste laboriosam iure
        voluptates sunt sint, possimus doloribus impedit nulla et? Consequuntur accusamus quia ex minima dolores animi
        omnis cupiditate.
      </p>
    </template>
    <template #footer>
      <button @click="onCloseModal">Close</button>
    </template>
  </Modal>
</template>