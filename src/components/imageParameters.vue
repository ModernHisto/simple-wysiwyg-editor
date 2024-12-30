<script setup>
import { ref, onMounted } from 'vue'

const prop = defineProps({
});
const emit = defineEmits();

const formDOM = ref(null);
</script>

<template>
  <div id="imageParameters">
    <form ref="formDOM">
      <div><input class="imageLink" placeholder="Ссылка на изображение" type="text" title="Ссылка на изображение"></div>
      <span>
        <div><label><input class="imageWidth" title="Ширина" aria-labelledby=""> Ширина</label></div>
        <div><label><input class="imageHeight" title="Высота"> Высота</label></div>
        <div><label><input class="imageMarginHorizontal" type="text" title="Горизонтальный отступ"> Горизонтальный отступ</label></div>
        <div><label><input class="imageMargitVertical" type="text" title="Вертикальный отступ"> Вертикальный отступ</label></div>
      </span>
      <div class="formButtons">
        <button onclick="event.preventDefault()" @click="emit('click_insert_image', formDOM)">Ок</button>
        <button onclick="event.preventDefault()" @click="emit('click_cancellation')">Отмена</button>
      </div>
    </form>
  </div>
</template>

<style scoped>
#imageParameters {
  display: flex;
  position: absolute;
  left: 38%;
  top: 40%;
  color: white;
  background-color:rgb(41, 41, 41);
  padding: 20px;
}

.imageLink {
  width: 350px;
  margin-bottom: 15px;
}

#imageParameters span div input {
  width: 50px;
}
.formButtons {
  margin-top: 20px;
  margin-left: 28%;
}
.formButtons button {
  width: 70px;
  height: 30px;
}
.formButtons :nth-child(1) {
  margin-right: 10px;
}
</style>