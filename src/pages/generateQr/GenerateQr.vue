<!-- eslint-disable space-before-function-paren -->
<script setup>
import QrcodeVue from 'qrcode.vue'
import { useRoute, useRouter } from 'vue-router'
import { ref, onMounted, computed } from 'vue'
import useFetchData from 'src/composables/useFetchData'

const { getUserById } = useFetchData()
const { result } = getUserById(4)

const user = computed(() => {
  return result.value?.getUser
})
console.log(user)
const router = useRouter()

const previousPage = ref('')
const goBack = () => {
  router.push(previousPage.value)
}

const route = useRoute()

onMounted(async () => {
  previousPage.value = route.params.from || '/'
})

// copy text
const copyText = () => {
  const textInput = document.getElementById('input')
  console.log(textInput.innerHTML)
  textInput.select()
  document.execCommand('copy')
}
</script>

<script>
export default {
  data () {
    return {
      value: 'https://example.com',
      size: 300
    }
  },
  components: {
    QrcodeVue
  }
}
</script>

<style scoped>
.error {
    font-weight: bold;
    color: red;
}

.barcode-format-checkbox {
    margin-right: 10px;
    white-space: nowrap;
}
</style>

<template>
<q-section class="q-pa-md">
  <q-section style="width: 350px; height: 350px; margin: 0 auto;">
    <q-item clickable v-ripple rounded style="width: 70px; height: 70px;"
      class="row q-pa-md q-flex justify-center items-center" @click="goBack">
      <q-avatar size="70px" icon="arrow_back" />
    </q-item>
  </q-section>
</q-section>
<div class='row wrap column justify-center items-center content-center' >
  <qrcode-vue :value="value" :size="size" level="H" class="my-auto"/>
  <p class="q-mt-xl">Scane address to receive payment</p>
  <q-card class="q-mt-md scan-adress__card">
    <span @click="copyText" id="input">{{ user?.addr }}</span>
  </q-card>
  <q-btn class="q-mt-xl q-px-xl" color="primary">Request payment</q-btn>
</div>
</template>

<style scoped>
.scan-adress__card {
  width: 336px;
  padding: 11px 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  cursor: pointer;
}
.scan-adress__card span {
  font-size: 16px;
}
</style>
