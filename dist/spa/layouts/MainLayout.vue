<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="bg-light-green-9">
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          Formulário
        </q-toolbar-title>

        <!--<div>Quasar v{{ $q.version }}</div>-->
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
         <div class="column flex-center q-ma-xs">
         <q-chip>
        <q-avatar size="50px">
          <img src="https://cdn.quasar.dev/img/boy-avatar.png">
        </q-avatar>
        John
      </q-chip>
      <br>
         <div class="full-width rounded-borders q-list q-list--bordered q-list--separator">
            <div class="q-item q-item-type row no-wrap">
                <div class="q-item__section column q-item__section--main justify-center">
                    <div class="q-item__label">Bem Vindo!!</div>
                </div>
              </div>
            </div>
          </div>
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksData = [
  {
    title: 'Cadastro',
    caption: 'Cadastro do Cliente',
    icon: 'school',
    link: '/'
  },
  {
    title: 'Clientes',
    caption: 'Informações sobre o cliente',
    icon: 'face',
    link: '/posts'
  }
]

export default {
  name: 'MainLayout',
  components: { EssentialLink },
  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData
    }
  }
}
</script>
