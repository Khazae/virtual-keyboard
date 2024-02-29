<script setup>
import VirtualKeyboard from "@/components/VirtualKeyboard.vue";
import { Button } from "@/components/ui/button";

useSeoMeta({
  title: "Virtual Keyboard",
});

const input = ref("");
const keyboardVisible = ref(false);

const onChange = (value) => {
  input.value = value;
};
const onKeyPress = (button) => {
  console.log("button", button);
};
const showKeyboard = () => {
  keyboardVisible.value = true;
};
const hideKeyboard = () => {
  keyboardVisible.value = false;
};
</script>

<template>
  <div class="wrapper">
    <div class="content">
      <Form class="form mb-5">
        <Input
          class="input mb-5"
          v-model="input"
          placeholder="Tap on the virtual keyboard to start"
          @focus="showKeyboard"
          @blur="hideKeyboard"
        />

        <Button class="button" type="submit">Поиск</Button>
      </Form>
    </div>
    <div class="keyboard" v-if="keyboardVisible" @mousedown.prevent>
      <VirtualKeyboard
        @onChange="onChange"
        @onKeyPress="onKeyPress"
        :input="input"
      />
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.content {
  width: 100%;
  max-width: 500px;
}
.input {
  width: 100%;
}

.button {
  width: 100%;
}
.keyboard {
  width: 100%;
  position: absolute;
  left: 0;
  bottom: 0;
}
</style>
