<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})
let msg_ref = ref("Vue+Vite")

const count = ref(0)

const test_fetchapi=async()=>{
  console.log("---test_fetchapi---")
  try{
    const res = await fetch("/testbp/testroute");
    const jsoned_res=await res.json()
    console.log(jsoned_res["flask-- @testbp.route(/testroute)"])
    console.log(jsoned_res["nowtime"])
    msg_ref.value=jsoned_res["nowtime"]
    return res
  }catch(e){
    console.log("error---")
    console.log(e)
  }
}
</script>

<template>
  <h1 @click="test_fetchapi">{{ msg_ref }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
