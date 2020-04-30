<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <v-list>
        <v-list-item-group>
          <v-list-item
            v-for="(route, index) in routes"
            :key="index"
            router
            :to="route.route"
            @click="drawer = false"
          >
            <v-list-item-content>
              <v-list-item-title>
                {{ route.name }}
              </v-list-item-title>
              <v-list-item-subtitle>
                test
              </v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
    <template>
      <v-app-bar
        src="https://picsum.photos/1920/1080?random"
        app
        dark
      >
        <template v-slot:img="{ props }">
          <v-img
            v-bind="props"
            gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
          ></v-img>
        </template>

        <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

        <v-toolbar-title>Title</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </v-app-bar>
    </template>

    <v-card
      width="450px"
      style="position: absolute; left: 50%; top: 50%; transform: translate(-50%, -50%)"
    >
      <v-card
        width="100px"
        height="40px"
        style="position: absolute; right: 30px; top: -20px"
      >
        <v-row>
          <v-col class="pa-0 text-right mt-2">
            <img
              src="https://upload.wikimedia.org/wikipedia/commons/2/27/Flag_of_Moldova.svg"
              alt="md" style="width: 42px; height: 26px" class="mr-1">
          </v-col>
          <v-col class="pa-0 text-left mt-2">
            <img
              src="https://upload.wikimedia.org/wikipedia/en/thumb/a/ae/Flag_of_the_United_Kingdom.svg/1200px-Flag_of_the_United_Kingdom.svg.png"
              alt="uk" style="width: 42px; height: 26px" class="ml-1">
          </v-col>
        </v-row>
      </v-card>
      <div>
        <div style="width: 90%; margin: auto" class="mt-8">
          <v-tabs
            color="#000"
            grow
          >
            <v-tab>
              Login
            </v-tab>
            <v-tab>
              Sign Up
            </v-tab>
            <v-tab-item>
              <v-expand-transition>
                <div>
                  <v-text-field
                    prepend-icon="mdi-account"
                    label="Login"
                    class="mt-2"
                  >
                  </v-text-field>
                  <v-text-field
                    prepend-icon="mdi-lock"
                    label="Password"
                    v-show="!forgot"
                    :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                    @click:append="show1 = !show1"
                    :type="show1 ? 'text' : 'password'"
                  >
                  </v-text-field>
                  <div>
                    <v-row>
                      <v-spacer></v-spacer>
                      <a class="mr-5" v-if="!forgot" @click="forgot = !forgot">
                        Forgot the password?
                      </a>
                      <a class="mr-5" v-if="forgot" @click="forgot = !forgot">
                        Back
                      </a>
                    </v-row>
                    <v-row class="mt-3">
                      <v-btn width="90%" style="margin: auto" v-if="!forgot">
                        Log in
                      </v-btn>
                      <v-btn width="90%" style="margin: auto" v-if="forgot">
                        Send recovery e-mail
                      </v-btn>
                    </v-row>
                  </div>
                </div>
              </v-expand-transition>
            </v-tab-item>
            <v-tab-item>
              <div>
                <v-text-field
                  label="Full name"
                  class="mt-2"
                  prepend-icon="mdi-account"
                >
                </v-text-field>
                <v-text-field
                  label="E-mail"
                  prepend-icon="mdi-email"
                >
                </v-text-field>
                <v-text-field
                  label="Password"
                  prepend-icon="mdi-lock"
                  :append-icon="show2 ? 'mdi-eye' : 'mdi-eye-off'"
                  @click:append="show2 = !show2"
                  :type="show2 ? 'text' : 'password'"
                >
                </v-text-field>
                <p class="body-2">
                  Min width is Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusantium cumque delectus
                </p>
                <v-text-field
                  label="Confirm password"
                  prepend-icon="mdi-lock-question"
                  :append-icon="show3 ? 'mdi-eye' : 'mdi-eye-off'"
                  @click:append="show3 = !show3"
                  :type="show3 ? 'text' : 'password'"
                >
                </v-text-field>
                <v-btn width="100%" style="margin: auto" dark>
                  Sign up
                </v-btn>
              </div>
            </v-tab-item>
          </v-tabs>
        </div>
      </div>
      <div>

      </div>
      <div class="ml-5 mr-5 mt-8">
      </div>
    </v-card>

  </v-app>
</template>

<script>
  /* eslint-disable */
  //import comp from './components/comp'
  export default {
    name: "App",
    components: {
      //comp
    },
    data: () => ({
      drawer: false,
      routes: [
        {name: "Home", info: "Something interesting", route: "/"},
        {name: "Test Field", info: "Not so interesting", route: "/test"}
      ],
      tab: null,
      text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
      forgot: false,
      show1: false,
      show2: false,
      show3: false
    })
  };
</script>
