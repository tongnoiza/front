<template>
      <v-footer
        v-bind="localAttrs"
        :padless="true"
      >
        <v-card
          flat
          tile
          width="100%"
          class="dark lighten-1 text-center align-center"
        >  <RegisterDialog />
          <!-- <v-card-text>
            <v-btn
              v-for="icon in icons"
              :key="icon"
              class="mx-4"
              icon
            >
              <v-icon size="24px">
                {{ icon }}
              </v-icon>
            </v-btn>
          </v-card-text> -->
          <v-divider></v-divider>
        </v-card>
      </v-footer>
  
      <!-- <v-row
        align="center"
        justify="center"
        class="ma-12"
      >
        <v-col
          cols="12"
          md="8"
        >
          <v-select
            v-model="variant"
            :items="items"
            clearable
            label="Variant"
          ></v-select>
  
          <v-checkbox
            v-model="padless"
            hide-details
            label="Padless"
          ></v-checkbox>
        </v-col>
      </v-row>   -->
  </template>
  <script>
    export default {
      data: () => ({
        icons: [
          'mdi-home',
          'mdi-email',
          'mdi-calendar',
          'mdi-delete',
        ],
        items: [
          'default',
          'absolute',
          'fixed',
        ],
        padless: false,
        variant: 'fixed',
      }),
      computed: {
        localAttrs () {
          const attrs = {}
         
          if (this.variant === 'default') {
            attrs.absolute = false
            attrs.fixed = false
          } else {
            attrs[this.variant] = true
          }
          return attrs
        },
      },
    }
  </script>