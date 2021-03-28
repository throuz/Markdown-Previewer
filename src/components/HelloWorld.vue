<template>
  <div id="wrap">
    <textarea
      name=""
      id="editor"
      cols="100"
      rows="30"
      v-model="inputContent"
    ></textarea>
    <div id="preview" v-html="outputContent"></div>
  </div>
</template>

<script lang="ts">
import { ref, defineComponent, watch } from "vue";
import marked from "marked";
export default defineComponent({
  name: "HelloWorld",
  setup: () => {
    const count = ref(0);
    const inputContent = ref("");
    let outputContent = ref("");
    marked.setOptions({
      breaks: true,
    });
    inputContent.value = `# header

## sub header

[link](http://example.com/ "Title")

\`inline code\`

    This is a code block.

Unorder list
*   Red
*   Green
*   Blue

Order list
1.  Bird
1.  McHale
1.  Parish

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

![Alt text](https://cn.vitejs.dev/logo.svg)

**bold text**`;
    outputContent.value = marked(inputContent.value);
    watch(inputContent, () => {
      outputContent.value = marked(inputContent.value);
    });

    return { count, inputContent, outputContent };
  },
});
</script>

<style scoped>
#wrap {
  display: flex;
  justify-content: center;
}
textarea {
  resize: none;
}
#preview {
  border: solid #000;
  width: 723px;
  box-sizing: border-box;
  padding: 30px;
}
</style>