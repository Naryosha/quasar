<template>
  <q-layout view="hHh lpr fFf">
    <q-header elevated>
      <q-toolbar class="q-gutter-md justify-around">
        <q-select dark color="yellow" borderless square v-model="fabDirection" :options="fabDirections" label="FAB open direction" style="min-width: 150px" />
        <q-select dark color="yellow" borderless square v-model="fabVerticalAlign" :options="fabVerticalAligns" label="FAB v-align" style="min-width: 150px" />
        <q-select dark color="yellow" borderless square v-model="fabLabelPosition" :options="fabLabelPositions" label="Label position" style="min-width: 150px" />
        <q-toggle dark color="yellow" v-model="fabExternalLabel" label="External label" />
        <q-toggle dark color="yellow" v-model="fabSquare" label="Square" />
        <q-toggle dark color="yellow" v-model="hideLabel" label="Hide label" />
        <q-toggle dark color="yellow" v-model="withLabelClass" label="Label class" />
      </q-toolbar>
    </q-header>

    <q-page-container>
      <q-page padding>

        <div v-for="i in 300" :key="i" class="q-pa-sm">
          Row {{ i }}
        </div>

        <q-page-sticky :position="stickyConfig.position" :offset="stickyConfig.offset">
          <q-fab
            :direction="fabDirection"
            color="primary"
            :label="`Actions aligned ${fabVerticalAlign}`"
            :label-position="fabLabelPosition"
            :actions-vertical-align="fabVerticalAlign"
            :square="fabSquare"
            :external-label="fabExternalLabel"
            :hide-label="hideLabel"
            :label-class="labelClass"
          >
            <q-fab-action
              class="white"
              color="green"
              icon="center_focus_weak"
              :square="fabSquare"
              :external-label="fabExternalLabel"
              :hide-label="hideLabel"
              :label-class="labelClass"
            />
            <q-fab-action
              class="white"
              color="red"
              icon="center_focus_weak"
              label="Anchor start"
              :label-position="fabLabelPosition"
              anchor="start"
              :square="fabSquare"
              :external-label="fabExternalLabel"
              :hide-label="hideLabel"
              :label-class="labelClass"
            />
            <q-fab-action
              class="white"
              color="red"
              icon="center_focus_weak"
              anchor="center"
              :square="fabSquare"
              :external-label="fabExternalLabel"
              :hide-label="hideLabel"
              :label-class="labelClass"
            />
            <q-fab-action
              class="white"
              color="blue"
              icon="center_focus_weak"
              label="Anchor center"
              :label-position="fabLabelPosition"
              anchor="center"
              :square="fabSquare"
              :external-label="fabExternalLabel"
              :hide-label="hideLabel"
              :label-class="labelClass"
            />
            <q-fab-action
              class="white"
              color="deep-orange"
              icon="center_focus_weak"
              anchor="end"
              :square="fabSquare"
              :external-label="fabExternalLabel"
              :hide-label="hideLabel"
              :label-class="labelClass"
            />
            <q-fab-action
              class="white"
              color="deep-orange"
              icon="center_focus_weak"
              label="Anchor end"
              :label-position="fabLabelPosition"
              anchor="end"
              :square="fabSquare"
              :external-label="fabExternalLabel"
              :hide-label="hideLabel"
              :label-class="labelClass"
            />
            <q-fab-action
              class="white"
              color="green"
              icon="center_focus_weak"
              :label-position="fabLabelPosition"
              :square="fabSquare"
              :external-label="fabExternalLabel"
              :hide-label="hideLabel"
              :label-class="labelClass"
            />
            <q-fab-action
              class="white"
              color="blue"
              icon="center_focus_weak"
              anchor="start"
              :square="fabSquare"
              :external-label="fabExternalLabel"
              :hide-label="hideLabel"
              :label-class="labelClass"
            />
            <q-fab-action
              class="white"
              color="purple"
              icon="center_focus_weak"
              label="Anchor default"
              :label-position="fabLabelPosition"
              :square="fabSquare"
              :external-label="fabExternalLabel"
              :hide-label="hideLabel"
              :label-class="labelClass"
            />
          </q-fab>
        </q-page-sticky>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  data () {
    return {
      fabDirection: 'up',
      fabVerticalAlign: 'center',
      fabExtended: true,
      fabExternalLabel: true,
      fabLabelPosition: 'right',
      fabSquare: false,
      hideLabel: false,
      withLabelClass: false,

      fabDirections: [ 'right', 'left', 'up', 'down' ],
      fabVerticalAligns: [ 'center', 'left', 'right' ],
      fabLabelPositions: [ 'right', 'left', 'top', 'bottom' ]
    }
  },

  computed: {
    labelClass () {
      if (this.withLabelClass === true) {
        return 'bg-white text-grey-8'
      }
    },

    stickyConfig () {
      if (this.fabDirection === 'up') {
        return {
          position: 'bottom',
          offset: [ this.fabVerticalAlign === 'center' ? 0 : 18, 18 ]
        }
      }

      if (this.fabDirection === 'down') {
        return {
          position: 'top',
          offset: [ this.fabVerticalAlign === 'center' ? 0 : 18, 18 ]
        }
      }

      if (this.fabDirection === 'left') {
        return {
          position: 'right',
          offset: [ 18, 0 ]
        }
      }

      return {
        position: 'left',
        offset: [ 18, 0 ]
      }
    }
  },

  methods: {
    logEvt (evt) {
      console.log(`@${evt.type}`, evt)
    }
  }
}
</script>
