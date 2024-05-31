<script setup>
import { ref } from 'vue'
let removeBox = ref(false)
</script>
<template>
  <div class="key-features" :style="{ right: removeBox ? '-500px' : '0' }">
    <div class="key-features-header">
      <h1>Key Features</h1>
      <button @click="removeBox = !removeBox" class="key-features-close-btn">
        <i class="fa-solid fa-square-xmark"></i>
      </button>
    </div>
    <hr />
    <div class="box-features-points">
      <h2>1) Responsive</h2>
      <h2>2) Client-side input validation</h2>
      <h2>3) Fast Loding time</h2>
      <h2>4) Easy to optimize code</h2>
    </div>
    <hr />
    <div class="reference">
      <h1>Reference</h1>
      <div class="box-reference-points">
        <h2>
          1) UI Blueprint :-
          <a
            href="https://www.figma.com/board/X5j2hgPlXwpeNMBqP7ijnf/Untitled?node-id=2%3A507&t=feRv8vYiNAHXnIYJ-1"
            target="_blank"
            >Figma Board</a
          >
        </h2>
        <h2>
          1) Modify UI :-
          <a
            href="https://www.figma.com/design/xs0mQHbFrU2OxA7dKpOLAi/Assignment---Frontend---Apr-2024-(Copy)-(Copy)?node-id=0%3A1&t=jdhmQUIH0dumIcP8-1"
            target="_blank"
            >Open Figma</a
          >
        </h2>
        <h2>3) GitHub Link :- <a href="">My GitHub</a></h2>
      </div>
    </div>
  </div>
</template>
<style scoped>
a {
  text-decoration: none;
}
.key-features {
  padding: 10px;
  background-color: rgb(255, 255, 255);
  position: absolute;
  right: 0;
  top: 0;
  padding: 5px 10px;
  border-bottom-left-radius: 5px;
  transition: all 0.3s;
}
.key-features hr {
  width: 10%;
  margin: auto;
}
.key-features-header {
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin-bottom: 10px;
}

.key-features-close-btn {
  font-size: 30px;
  border: none;
}

.key-features-close-btn:hover {
  color: #373737;
  cursor: pointer;
}
.box-features-points {
  margin-bottom: 10px;
}
.reference > h1 {
  text-align: center;
}
.box-reference-points {
  margin-bottom: 10px;
}
/*  ..............................Media Query Here............................ */
@media only screen and (max-width: 1510px) {
  .key-features {
    display: none;
  }
}
</style>
