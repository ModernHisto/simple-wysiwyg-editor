<script setup>
import { ref, onMounted} from 'vue'
import EditorialControlPanel from "./components/EditorialControlPanel.vue";

const iframeSrc = ref('../../editorialStaff.html');
const iframe = ref(null);
setTimeout(() => {  //Делаем так, что-бы первый клик по документу создавал <p> 
  function firstParagraph() {
    iframe.value.contentDocument.execCommand('formatBlock', false, 'p');
    iframe.value.contentDocument.removeEventListener('click', firstParagraph);
  };
  iframe.value.contentDocument.addEventListener("click", firstParagraph);
  }, 50)
</script>

<template>
  <div class="wraper">
    <EditorialControlPanel
    :iframe_prop="iframe"
    />
    <iframe srcdoc='<!DOCTYPE html> <html dir="ltr" lang="ru"> <head> <meta charset="utf-8" /> <title>editorialStaff</title> <style> body { overflow-wrap: break-word; } </style> <script> document.designMode = "on" </script> </head> <body spellcheck="false"> </body> </html>' ref="iframe" frameborder="0" title="Редактор" height="700" width="100%">
      <p>iframe не поддерживается</p>
    </iframe>

  </div>
</template>

<style scoped>
.wraper {
  margin: 77px 0 0 0;
}
</style>