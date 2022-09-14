<template>
  
      <v-dialog
        v-model="dialog"
        persistent
        max-width="600px"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            color="dark"
            dark
            v-bind="attrs"
            v-on="on"
            text
          >
           About Us
          </v-btn>
        </template>
        <v-card>
          <v-card-title>
            <span class="text-h5">เกี่ยวกับเรา</span>
          </v-card-title>
          <v-card-text>
          
             Lorem ipsum dolor sit amet consectetur, adipisicing elit. Iure minima nesciunt sequi ipsum quas nulla temporibus voluptatum dicta quis perspiciatis nobis veniam, nemo necessitatibus soluta! Mollitia sint perspiciatis quaerat. Adipisci! Lorem ipsum, dolor sit amet consectetur adipisicing elit. Earum sequi aliquam enim debitis illum consequuntur necessitatibus, at dolorum nemo repellat fuga magni eum possimus iste officiis impedit tempora eveniet temporibus? 
          
        
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              color="blue darken-1"
              text
              @click="dialog = false"
            >
              Close
            </v-btn>
            <v-btn
              color="blue darken-1"
              text
              @click="dialog = false"
            >
              Save
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>

  </template>

<script>
    export default {
      data: () => ({
        dialog: false,
      }),
    }
  </script>