<template>
  <h1>{{ msg }}</h1>

  <p>
    Recommended IDE setup:
    <a href="https://code.visualstudio.com/" target="_blank">VSCode</a>
    +
    <a
      href="https://marketplace.visualstudio.com/items?itemName=octref.vetur"
      target="_blank"
    >
      Vetur
    </a>
    or
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
    (if using
    <code>&lt;script setup&gt;</code>)
  </p>

  <p>See <code>README.md</code> for more information.</p>

  <p>
    <a href="https://vitejs.dev/guide/features.html" target="_blank">
      Vite Docs
    </a>
    |
    <a href="https://v3.vuejs.org/" target="_blank">Vue 3 Docs</a>
  </p>

  <button type="button" @click="count++">count is: {{ count }}</button>
  <p>
    Edit
    <code>components/HelloWorld.vue</code> to test hot module replacement.
  </p>
</template>

<script lang="ts">
import { ref, defineComponent } from 'vue'
import { useStore } from '../store/index'
import { useRouter } from 'vue-router'
export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: {
      type: String,
      default: '随意内容'
    }
  },
  watch: {
    '$route.params': function(toParams, preParams) {
      console.log(toParams)
      console.log(preParams)
    }
  },
  mounted() {
    console.log(this.$route)
    console.log(this.$router)
  },
  setup(props) {
    const count = ref(0)
    const store = useStore()
    const router = useRouter()
    console.log(router)
    return { count }
  }
})
</script>

<style scoped lang="less">
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
