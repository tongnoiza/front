<template>
    <v-row align="center">
      <v-item-group
        v-model="window"
        class="shrink mr-6"
        mandatory
        tag="v-flex">
        <v-item
          v-for="n in length"
          :key="n"
          v-slot="{ active, toggle }"
        >
          <div>
            <v-btn
              :input-value="active"
              icon
              @click="toggle">
              <v-icon>mdi-record</v-icon>
            </v-btn>
          </div>
        </v-item>
      </v-item-group>
      <v-col>
        <v-window
          v-model="window"
          class="elevation-1"
          vertical
          :continuous="true"
        >
          <v-window-item
            v-for="n in length"
            :key="n"
          >
            <v-card flat>
              <v-card-text>
                <v-row
                  class="mb-4"
                  align="center"
                >
                  <v-avatar
                    color="grey"
                    class="mr-4"
                  ></v-avatar>
                  <strong class="text-h6">Title {{ n }}</strong>
                  <v-spacer></v-spacer>
                  <v-btn icon>
                    <v-icon>mdi-account</v-icon>
                  </v-btn>
                </v-row>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptates amet tenetur saepe itaque, omnis asperiores ab maxime suscipit pariatur, ullam labore laborum eligendi deserunt consequatur nostrum ad vel at hic!</p>
               
              </v-card-text>
            </v-card>
          </v-window-item>
        </v-window>
      </v-col>
    </v-row>
  </template>
  <script>
    export default {
        props:{
            data:{
                type:[],
                require:true
            }
        },
      data(){return{
        length: 20,
        window: 20,
      }}  ,
   async activated(){
  await this.set()
      },
      methods:{
        set(){
        this.length = 5 
        this.window = 5
        console.log('this data form child ',this.props.data)
        }
      }
    }
  </script>