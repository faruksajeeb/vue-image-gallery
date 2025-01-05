<template>
    <div class="gallery">
        <div class="gallery-item" v-for="(image, index) in images" :key="index">
            <img :src="image" @click="openModal(index)" alt="Gallery Image">
        </div>

        <div v-if="showModal" class="modal" @click="closeModal">
            <span class="close">&times;</span>
            <img class="modal-content" :src="currentImage">
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            images: [
                'https://picsum.photos/id/237/200/300',
                'https://picsum.photos/seed/picsum/200/300',
                'https://picsum.photos/200/300?grayscale'
            ],
            showModal: false,
            currentImage: '',
        }
    },
    methods: {
        openModal(index) {
            this.currentImage = this.images[index];
            this.showModal = true;
        },
        closeModal() {
            this.showModal = false;
        }
    }
}
</script>

<style>
.gallery {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
.gallery-item img {
  width: 150px;
  cursor: pointer;
}
.modal {
  display: flex;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.8);
  justify-content: center;
  align-items: center;
}
.modal-content {
  max-width: 80%;
  max-height: 80%;
}
.close {
  position: absolute;
  top: 10px;
  right: 25px;
  font-size: 35px;
  color: white;
  cursor: pointer;
}
</style>