<template>
  <q-layout view="lHr LpR lFr">

    <q-header bordered class="bg-grey-2 text-grey-8">
      <q-toolbar>
          <div class="left">
          <span class="text-bold">Ahmet Kara'</span>
          <span>yazıyor...</span>
          </div>
          <q-space />
          <div class="right">
            <q-icon style="border-left : 1px solid #ccc; height: 40px" class="q-pa-sm cursor-pointer" size="sm" name="star"/>
            <q-icon style="border-left : 1px solid #ccc; height: 40px" class="q-pa-sm cursor-pointer" size="sm" name="phone"/>
            <q-icon style="border-left : 1px solid #ccc; height: 40px" class="q-pa-sm cursor-pointer" size="sm" name="videocam"/>
          </div>
      </q-toolbar>
    </q-header>

    <q-drawer content-class="bg-blue-grey-10" show-if-above v-model="left" side="left">
      <div class="q-pa-md">
        <q-input standout="bg-blue-grey-7" input-class="text-white" class="bg-blue-grey-9" style="border-radius: 30px" v-model="search" clearable dense rounded>
        <template v-slot:prepend>
          <q-icon color="white" name="search" />
        </template>
      </q-input>
      </div>
       <q-separator color="blue-grey-9" />
       <q-list bordered class="rounded-borders text-grey-4" style="max-width: 350px">
           <Message :message="user" />
    </q-list>
    </q-drawer>

    <q-drawer show-if-above v-model="right" side="right" bordered>
      <div class="columns text-center">
        <div class="row justify-between">
          <q-icon name="forum" color="blue" size="sm"/>
          <q-btn flat round icon="more_horiz" dense>
          <q-menu fit>
          <q-list dense style="min-width: 100px">
            <q-item clickable v-close-popup>
              <q-item-section>Profili Görüntüle</q-item-section>
            </q-item>
            <q-item clickable v-close-popup>
              <q-item-section>Bildirimleri sessize al</q-item-section>
            </q-item>
            <q-item clickable v-close-popup>
              <q-item-section>Mesajları Temizle</q-item-section>
            </q-item>
             <q-item clickable v-close-popup>
              <q-item-section>Sohbeti sil</q-item-section>
            </q-item>
            <q-item clickable v-close-popup>
              <q-item-section>Engelle</q-item-section>
            </q-item>
          </q-list>
        </q-menu>
        </q-btn>
        </div>
        <q-avatar size="100px">
         <img src="https://media.wired.com/photos/5932933926780e6c04d2cc4d/master/pass/ff_musk4_f.jpg">
        </q-avatar>
      <p class="q-pa-sm text-bold text-grey-8 q-ma-none" style="font-size: 16px;">Elon Musk</p>
      <span class="text-grey-8 text-caption" style="font-size: 13px;"> Spacex, Tesla</span>
      </div>
      <q-separator class="q-my-sm"></q-separator>
    </q-drawer>

    <q-page-container class="bg-blue-grey-2">
      <router-view />
    </q-page-container>

    <q-footer bordered class="bg-blue-grey-1 text-grey-8">
      <div class="row no-wrap q-pa-md items-center">
        <q-btn round unelevated icon="emoji_emotions" flat/>
        <q-btn round unelevated class="cursor-pointer q-mr-sm" icon="attachment" size="md" flat/>
        <q-input class="full-width" borderless v-model="message" dense placeholder="Bir mesaj yazın" />
        <q-btn unelevated round icon="send" flat/>
      </div>
    </q-footer>

  </q-layout>
</template>

<script>
import Message from 'components/Message'
export default {
  name: 'layout',
  data () {
    return {
      left: false,
      right: false,
      search: '',
      message: '',

      user: {
        photoURL: 'https://pbs.twimg.com/profile_images/669103856106668033/UF3cgUk4_400x400.jpg',
        isOnline: true,
        displayName: 'Jeff Bezos',
        message: [
          {
            message: 'xxxx',
            date: '2021-04-14 02:20:10'
          }
        ]

      }
    }
  },
  components: {
    Message
  }
}
</script>
