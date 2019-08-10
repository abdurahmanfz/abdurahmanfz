<template>
  <v-app style="background: #ECEFF1">
    <v-app-bar app dark>
      <v-toolbar-title class="Title text-sentencecase">
        <span class="font-weight-bold" style="color: #FDD835">Curriculum</span>
        <span class="font-weight-light" style="color: #FDD835">Vitae</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn dark icon @click="drawer = !drawer">
        <v-icon color="yellow darken-1">mdi-contacts</v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer 
      clipped
      temporary
      app
      v-model="drawer"
      fixed class="elevation-0"
    >
      <v-card flat>
        <v-card-text class="pb-0">
            <!-- max-height="150px" -->
          <v-avatar width="220" height="auto">
            <v-img 
              avatar
              :aspect-ratio="2/2"
              :src="require('../src/assets/santolo.jpg')"
            ></v-img>
          </v-avatar>
        </v-card-text>
      </v-card>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            Fauzan Abdurrahman <v-icon color="blue lighten-2">mdi-check-decagram</v-icon>
          </v-list-item-title>
          <v-list-item-subtitle>
            Front-end Web Developer
          </v-list-item-subtitle>
          <v-list-item-subtitle>
            zandt55@gmail.com
          </v-list-item-subtitle>
          <v-list-item-subtitle>
            abdrhmnfz@gmail.com
          </v-list-item-subtitle>
          <v-list-item-subtitle>
            (+62) 889 7060 1825
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          link :href="item.to" target="_blank"
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-content>
      <CoreView/>
      <v-container>
      </v-container>
    </v-content>

    <v-footer style="height: 40px; color: #FDD835" dark inset fixed>
      Made with &nbsp;<v-icon small color="green">mdi-vuejs</v-icon>&nbsp; + &nbsp;<v-icon small color="blue">mdi-vuetify</v-icon>&nbsp; = &nbsp;<v-icon small color="red">mdi-heart</v-icon>&nbsp;
    </v-footer>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',
  components: {
    // HelloWorld,
    CoreView: () => import('@/components/View')  
  },
  
  data: () => ({
    drawer: false,
    items: [
      { icon: 'mdi-instagram', text: 'Instagram', to: 'https://www.instagram.com/abdurahmanfz/'},
      { icon: 'mdi-github-box', text: 'Github', to: 'https://github.com/abdurahmanfz'},
      { icon: 'mdi-medium', text: 'Medium', to: 'https://medium.com/@abdurahmanfz'},
      { icon: 'mdi-linkedin', text: 'Linkedin', to: 'https://www.linkedin.com/in/fauzan-abdurrahman-b0224a136/'},
      { icon: 'mdi-account', text: 'About', to: '/about'},
      // { icon: 'mdi-github-box', text: 'About', to: 'https://github.com/abdurahmanfz'},
    ]
  }),
};
</script>
