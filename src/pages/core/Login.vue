<template>
  <v-app id="login" class="secondary">
    <notifications></notifications>
    <v-content>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4 lg4>
            <v-card class="elevation-1 pa-3">
              <v-card-text>
                <div class="layout column align-center">
                  <img src="static/logo.png" alt="Vue Material Admin" width="180" height="180" />
                  <h1 class="flex my-4 primary--text">Vue Admin Template</h1>
                </div>
                <v-form>
                  <v-text-field
                    append-icon="person"
                    name="login"
                    label="Login"
                    type="text"
                    v-model="userEmail"
                    :error="error"
                    :rules="[rules.required]"
                  />
                  <v-text-field
                    :type="hidePassword ? 'password' : 'text'"
                    :append-icon="hidePassword ? 'visibility_off' : 'visibility'"
                    name="password"
                    label="Password"
                    id="password"
                    :rules="[rules.required]"
                    v-model="password"
                    :error="error"
                    @click:append="hidePassword = !hidePassword"
                  />
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn block color="primary" @click="login" :loading="loading">Login</v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
      <v-snackbar v-model="showResult" :timeout="2000" top>{{ result }}</v-snackbar>
    </v-content>
  </v-app>
</template>

<script>
import axios from "axios";
import router from "../../router";
import EventBus from "./EventBus";
export default {
  data() {
    return {
      loading: false,
      userEmail: "asd@gmail.com",
      password: "asd",
      hidePassword: true,
      error: false,
      showResult: false,
      result: "",
      rules: {
        required: value => !!value || "Required."
      }
    };
  },

  methods: {
    login() {
      //   console.log(this.userEmail);
      //   console.log(this.password);
      axios
        .post("users/login", {
          email: this.userEmail,
          password: this.password
        })
        .then(res => {
          if (res.data.error == undefined) {
            localStorage.setItem("token", res.data.token);
            // this.email = "";
            // this.password = "";
            router.push({ name: "Profile" });
          } else {
            this.$notify({
              group: "g-login",
              type: "error",
              title: "Important message",
              text: "Hello user! This is a notification!"
            });
          }
          //   localStorage.setItem("token", res.data.token);

          //   this.email = "";
          //   this.password = "";
        })
        .catch(err => {
          //   this.notifyVue(
          //     "danger",
          //     "Authentication Error",
          //     "Wrong password, please try again"
          //   );
          console.log("error : ", err);
        });
      this.emitMethod();
    },
    emitMethod() {
      EventBus.$emit("logged-in", "loggedin");
    }
  }
};
</script>

<style scoped lang="css">
#login {
  height: 50%;
  width: 100%;
  position: absolute;
  top: 0;
  left: 0;
  content: "";
  z-index: 0;
}
</style>
