<template>
    <div>
  <q-item clickable v-ripple>
        <q-item-section avatar>
          <q-avatar size="48px">
            <img :src="message.photoURL">
            <q-badge v-if="message.isOnline" floating rounded color="green" label="." text-color="green">x</q-badge>
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label lines="1">{{ message.displayName }}</q-item-label>
          <q-item-label caption class="text-grey-6" lines="2">{{message.message[0].message}}</q-item-label>
        </q-item-section>

        <q-item-section side top>

          <q-btn dense flat color="grey-6" icon="more_horiz"></q-btn>
          <q-item-label caption class="text-grey-7">{{getDate}}</q-item-label>
        </q-item-section>
      </q-item>
        <q-separator inset="item" color="blue-grey-9" />
      </div>
</template>

<script>
import { date } from 'quasar'
export default {
  name: 'Message',
  props: {
    message: { type: Object, required: true }
  },
  computed: {
    getDate () {
      return date.getDateDiff(new Date(), this.message.message[0].date, 'minutes')
    }
  }
}
</script>
