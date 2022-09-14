<template>
  <v-dialog v-model="dialog" persistent max-width="600px">
    <template v-slot:activator="{ on, attrs }">
      <v-btn color="dark" dark v-bind="attrs" v-on="on" text>
        <v-icon small>mdi-account-plus</v-icon> &nbsp;
        <v-skeleton-loader type="button"> Register</v-skeleton-loader>
      </v-btn>
    </template>
    <v-card>
      <v-card-title>
        <span class="text-h5"
          ><v-icon>mdi-badge-account</v-icon> User Profile</span
        >
      </v-card-title>
      <v-card-text>
        <v-container>
          <v-row>
            <v-col cols="3" sm="6" md="4">
              <v-text-field
                v-model="form.user_firstname"
                label="Legal first name*"
                required
                :disabled="mode=='view'"
              ></v-text-field>
            </v-col>
            <v-col cols="3" sm="6" md="4">
              <v-text-field
                v-model="form.user_middlename"
                label="Legal middle name"
                hint="example of helper text only on focus"
                :disabled="mode=='view'"
              ></v-text-field>
            </v-col>
            <v-col cols="3" sm="6" md="4">
              <v-text-field
                v-model="form.user_lastname"
                label="Legal last name*"
                hint="example of persistent helper text"
                persistent-hint
                required
                :disabled="mode=='view'"
              ></v-text-field>
            </v-col>
            <v-col cols="12">
              <v-text-field
                v-model="form.user_email"
                label="Email*"
                required
                :disabled="mode=='view'"
              ></v-text-field>
            </v-col>
            <v-col cols="12">
              <v-text-field
                v-model="form.user_password"
                label="Password*"
                type="password"
                required
                :disabled="mode=='view'"
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="6">
              <v-select
                v-model="form.user_age"
                :items="age"
                label="Age*"
                required
                :disabled="mode=='view'"
              ></v-select>
            </v-col>
            <v-col cols="12" sm="6">
              <v-autocomplete
                v-model="form.sports_id"
                :items="listsports"
                label="Interests"
                multiple
                :disabled="mode=='view'"
              ></v-autocomplete>
            </v-col>
          </v-row>
        </v-container>
        <small>*indicates required field</small>
      </v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn text @click="dialog = false" color="red"> Close </v-btn>
        <v-btn v-if="mode!='view'" color="green" text @click="save()"
          ><v-icon>mdi-content-save-move</v-icon>&nbsp;Save
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
  <!-- about Us -->
</template>

<script>
export default {
  name: "RegistereDialog",
  async fetch() {
    this.SportsList = await this.$axios.$get("http://yamq.dyndns.org:3002/getSportsList");
    this.listsports = await this.SportsList.map((list) => list.sports_name);
    for (let a = 1; a <= 80; a++) this.age.push(a);
  },
  data() {
    return {  mode:'',
      age: [],
      dialog: false,
      pageabout: false,
      form: {},
      data: {},
      SportsList: [],
      listsports: [],
    };
  },
  methods: {
  async test(mode,data) {
    this.mode =mode
   let formdata = await this.$axios.$get('http://yamq.dyndns.org:3002/register?user_id='+data) 
   this.form  = formdata.data[0]
      this.dialog = true
    },
    async save() {
      let arr = [];
      // mapping id
      this.SportsList.forEach((x) => {
        this.form.sports_id.forEach((v) => {
          if (x.sports_name == v) {
            arr.push(x.sports_id);
          }
        });
      });

      this.form.sports_id = 1;
      this.$axios
        .$post("http://yamq.dyndns.org:3002/register", this.form)
        .then(async (resp) => {
          if (await resp.status) this.dialog = false;
        })
        .catch((err) => console.log("err log ", err));
    },
  },
  created() {
    this.$nuxt.$on("view", (mode,data) => this.test(mode,data));
  },
};
</script>
