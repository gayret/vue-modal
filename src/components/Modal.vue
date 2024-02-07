<script setup>
const isVisibleModal = defineModel({ type: Boolean, default: false }) // define two way binding

const props = defineProps({
  width: {
    type: String,
    default: '40rem'
  }
})

// close modal when click on backdrop
const onCloseModal = (e) => {
  if (e.srcElement.classList.contains('backdrop')) {
    isVisibleModal.value = false
  }
}
</script>

<template>
  <div v-if="isVisibleModal" class="backdrop" @click="onCloseModal">
    <div class="modal">
      <section class="header">
        <slot name="header" />
      </section>
      <section class="main">
        <slot name="content" />
      </section>
      <section class="footer">
        <slot name="footer" />
      </section>
    </div>
  </div>
</template>

<style scoped>
.backdrop {
  width: 100vw;
  height: 100vh;
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal {
  background-color: rgba(0, 0, 0);
  padding: 2rem;
  border-radius: .5rem;
  width: v-bind(width);
  display: flex;
  flex-direction: column;
  gap: 1em;
}

.header {
  font-weight: bold;
}

.footer {
  margin-left: auto;
}
</style>