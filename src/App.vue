<script setup>
const str = '&amp;1';
const regex = /&amp;/
const regex2 = new RegExp(/&amp;/)

const replace = (text) => {
  return text.replace(regex, 'setupFunc')
}
</script>

<template>
  <p>
    original: {{str}}
    <br>
    directly: {{str.replace(/&amp;/, 'test1')}}
    <br>
    directly: {{str.replace(/&amp;/, 'test2')}}
    <br>
    directly, but with inline new Regex: {{str.replace(new RegExp(/&amp;/), 'inlineRegex')}}
    <br>
    call func in the setup: {{replace(str)}}
    <br>
    inline func: {{((text)=>
    	text.replace(/&amp;/, 'inlineFunc')
    )(str)}}
    <br>
    directly, but use regex in the setup: {{str.replace(regex, 'test3')}}
    <br>
    directly, but with new Regex in the setup: {{str.replace(regex2, 'test4')}}
  </p>
  v-html: <p v-html="str"></p>
  v-text: <p v-text="str"></p>
</template>