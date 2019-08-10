<template>
  <v-container>
    <v-layout column justify-center align-center>
      <v-flex xs12>
        <v-card width="800px" class="elevation-0">
          <v-card-title class="title">
            Profile
          </v-card-title>
          <v-card-text>
            <v-layout wrap>
              <v-flex xs12 sm3>
                <v-img right
                  width="150px"
                  height="150px"
                  :aspect-ratio="2/2"
                  :src="require('../assets/santolo.jpg')"
                ></v-img>
              </v-flex>
              <v-flex xs12 sm9>
                <p class="subtitle-1">
                  <span>Full Name : </span> <span>Fauzan Abdurrahman</span> <br>
                  <span>Birthplace : </span> <span>Bandung</span> <br>
                  <span>Birthdate : </span> <span>31st May 1999</span>
                </p>
              </v-flex>
            </v-layout>
          </v-card-text>
        </v-card>

        <v-card width="800px" class="my-4 elevation-0">
          <v-card-title class="title">
            Hobbies
          </v-card-title>
          <v-card-text>
            <v-layout wrap>
              <template v-for="item in hobbies">
                <v-flex xs12 sm4 :key="item.id">
                  <v-icon>{{item.icon}}</v-icon> &nbsp;
                  <span class="subtitle-2">{{item.title}}</span>
                  <v-tooltip left bottom>
                    <template v-slot:activator="{ on }">
                      <p v-on="on" class="ma-0 text-truncate">
                        <v-rating
                          dense readonly
                          :empty-icon="emptyIcon"
                          :full-icon="fullIcon"
                          :half-icon="halfIcon"
                          :length="item.count"
                          background-color="red lighten-3"
                          half-increments color="red darken-2"
                          v-model="item.rate">
                        </v-rating>
                      </p>
                    </template>
                    <span>{{item.description}}</span>
                  </v-tooltip>
                  <!-- <v-img right
                    width="150px"
                    height="150px"
                    :aspect-ratio="2/2"
                    :src="require('../assets/pas_foto.jpeg')"
                  ></v-img> -->
                </v-flex>
              </template>
            </v-layout>
          </v-card-text>
        </v-card>      

        <v-card width="800px" class="my-4 elevation-0">
          <v-card-title class="title">
            Education
          </v-card-title>
          <v-card-text>
            <v-layout wrap>
              <template v-for="item in education">
                <v-flex xs12 sm4 :key="item.id" style="padding: 8px 4px">
                  <v-icon>{{item.icon}}</v-icon> &nbsp;
                  <span class="subtitle-2">{{item.title}}</span>
                  <br><br>
                  <!-- <v-img right
                    width="100%"
                    height="150px"
                    style="margin: 8px 0"
                    :aspect-ratio="2/2"
                    :src="require('../assets/pas_foto.jpeg')"
                  ></v-img> -->
                  <iframe :src="item.loc" width="100%" height="100px" frameborder="0" style="border:0" allowfullscreen></iframe>
                  <v-hover>
                    <span 
                      class="subtitle-2"
                      slot-scope="{ hover }" 
                      style="cursor: pointer"
                    >
                      <a :href="item.link" target="_blank" rel="noopener noreferrer">
                        <v-icon :color="`${hover ? 'blue' : 'grey'}`">mdi-map-marker</v-icon> &nbsp;
                        <span  :class="`${hover ? 'textblue' : 'textgrey'}`">
                          {{item.name}}
                        </span>
                      </a>
                    </span>
                  </v-hover>
                </v-flex>
              </template>
            </v-layout>
          </v-card-text>
        </v-card>      

        <v-card width="800px" class="my-4 elevation-0">
          <v-card-title class="title">
            Skills
          </v-card-title>
          <v-card-text>
            <v-list-item v-for="item in skills" :key="item.id" dense>
              <v-list-item-content>
                <v-list-item-title>
                  <!-- <div v-html="item.title"></div> -->
                  {{item.title}}
                </v-list-item-title>
                <v-list-item-subtitle>
                  <v-progress-linear
                    :color="item.color"
                    :background-color="item.bgColor"
                    :length="item.count"
                    v-model="item.rate"
                  ></v-progress-linear>
                </v-list-item-subtitle>
              </v-list-item-content>
              <v-list-item-action>
                {{ item.rate }} / 100
              </v-list-item-action>
            </v-list-item>
          </v-card-text>
        </v-card>
        
        <v-card width="800px" class="my-4 elevation-0">
          <v-card-title class="title">
            Language Skills
          </v-card-title>
          <v-card-text>
            <v-card v-for="item in languages" :key="item.id" flat>
              <v-card-text class="pb-0 subtitle-1">
                <span style="color: black;">{{item.title}}</span>
              </v-card-text>
              <v-card-text class="pt-0">
                <v-layout wrap>
                  <v-flex xs4>
                    <span class="subtitle-4">Writing</span> <br>
                    <v-progress-circular
                      :value="item.score.writing"
                      color="error"
                      size="100"
                      width="15"
                    >{{item.score.writing}}</v-progress-circular>
                  </v-flex>
                  <v-flex xs4>
                    <span class="subtitle-4">Speaking</span> <br>
                    <v-progress-circular
                      :value="item.score.speaking"
                      color="blue"
                      size="100"
                      width="15"
                    >{{item.score.speaking}}</v-progress-circular>
                  </v-flex>
                  <v-flex xs4>
                    <span class="subtitle-4">Reading</span> <br>
                    <v-progress-circular
                      :value="item.score.reading"
                      color="orange"
                      size="100"
                      width="15"
                    >{{item.score.reading}}</v-progress-circular>
                  </v-flex>
                </v-layout>
              </v-card-text>
              <v-divider></v-divider>
            </v-card>
            <!-- <v-list-item dense>
              <v-list-item-content>
                <v-list-item-title>
                </v-list-item-title>

                <v-list-item-subtitle>
                  <v-progress-linear
                    :color="item.color"
                    :background-color="item.bgColor"
                    :length="item.count"
                    v-model="item.score.writing"
                  ></v-progress-linear>
                </v-list-item-subtitle>

              </v-list-item-content>
              <v-list-item-action>
                {{ item.rate }} / 100
              </v-list-item-action>
            </v-list-item> -->
          </v-card-text>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<style scoped>
  .textblue{
    color: #2196F3 !important;
  }
  .textgrey{
    color: #9E9E9E !important;
  }

  .v-list-item__content {
    padding: 0px !important;
  }
  
  a{
    text-decoration: none
  }
</style>

<script>
export default {
  data: () => ({
    
    hobbies: [
      { id: 1, icon: 'mdi-wallet-travel', title:'Traveling', count: 5, rate: 4, description: '4/5' },
      { id: 2, icon: 'mdi-camera', title:'Photography', count: 5, rate: 4, description: '4/5' },
      { id: 3, icon: 'mdi-code-not-equal-variant', title:'Coding', count: 10, rate: 8.5, description: 'Nope, just kidding. its 4.5/5 !' },
    ],

    education: [
      { 
        id: 1, icon: 'mdi-face', title:'Elementary', 
        name: "Madrasah Ibtidaiyah Zakaria",
        loc: 'https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d15842.230896910412!2d107.647387!3d-6.94334!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x47ed49f868dc1124!2sMadrasah+Ibtidaiyah+(MIS)+Zakaria+III!5e0!3m2!1sen!2sid!4v1565452687136!5m2!1sen!2sid', 
        link: 'https://goo.gl/maps/KX5EK3t4TFzgTqt89'
      },
      { 
        id: 2, icon: 'mdi-school', title:'Middle', 
        name: "SMPN 18 Bandung",
        loc: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3960.4857867550936!2d107.63948981436766!3d-6.951880369990342!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e68e8412514362f%3A0x8540da1ef80a72c1!2sSMPN+18+Bandung!5e0!3m2!1sen!2sid!4v1565453031245!5m2!1sen!2sid', 
        link: 'https://goo.gl/maps/aPDuNq5RrdXjHQrg8'
      },
      { 
        id: 3, icon: 'mdi-laptop-windows', title:'Vocational', 
        name: "SMKN 4 Bandung",
        loc: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3960.5775726308284!2d107.62689201436757!3d-6.9409817698746235!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e68e86413eb50ad%3A0xf9930b5268e3fee1!2sVocational+High+School+4+Bandung!5e0!3m2!1sen!2sid!4v1565453171800!5m2!1sen!2sid', 
        link: 'https://goo.gl/maps/KxzUSotxJQovMEjRA'
      },
      { 
        id: 4, icon: 'mdi-city', title:'University', 
        name: "STMIK 'AMIK Bandung'",
        loc: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3960.7981336608864!2d107.63607781477282!3d-6.91472259500378!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e68e7c48c5feaaf%3A0x3daa8543173632b1!2sSTMIK+AMIKBANDUNG!5e0!3m2!1sen!2sid!4v1565453781751!5m2!1sen!2sid', 
        link: 'https://g.page/AMIKBANDUNG?share'
      },
      { 
        id: 5, icon: 'mdi-whistle', title:'Non-Formal', 
        name: "Santri Siap Guna", 
        loc: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3961.215708193063!2d107.5876532143669!3d-6.864733969070687!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e68e6bc4dd69ba5%3A0xea582de3c7a89e25!2sSantri+Siap+Guna+Daarut+Tauhiid!5e0!3m2!1sen!2sid!4v1565453868742!5m2!1sen!2sid',
        link: 'https://goo.gl/maps/MTPZve9G6ueRszjAA'
      },
    ],

    skills: [
      { 
        id: 1, title: 'Photoshop', count: 10, rate: 65,
        color: 'blue', bgColor: 'blue lighten-3',
      },
      { 
        id: 2, title: 'Corel Draw', count: 10, rate: 80,
        color: 'green', bgColor: 'green lighten-3',
      },
      { 
        id: 3, title: 'Vue Js', count: 10, rate: 85,
        color: 'teal darken-2', bgColor: 'teal lighten-3',
      },
      { 
        id: 4, title: 'Nuxt Js', count: 10, rate: 85,
        color: 'green darken-1', bgColor: 'green lighten-3',
      },
      { 
        id: 4, title: 'Sketch Up', count: 10, rate: 70,
        color: 'red lighten-1', bgColor: 'red lighten-3',
      },
      { 
        id: 4, title: 'Blender', count: 10, rate: 40,
        color: 'orange lighten-1', bgColor: 'orange lighten-3',
      },
    ],

    languages: [
      { 
        id: 1, 
        title: 'Bahasa', 
        score: {
          writing: 90, speaking: 95, reading: 100
        }
      },
      { 
        id: 2, 
        title: 'Sundanesse', 
        score: {
          writing: 90, speaking: 95, reading: 100
        }
      },
      { 
        id: 3, 
        title: 'English', 
        score: {
          writing: 80, speaking: 75, reading: 90
        }
      },
      { 
        id: 4, 
        title: 'Arabic', 
        score: {
          writing: 70, speaking: 40, reading: 60
        }
      }
    ],

    emptyIcon: 'mdi-heart-outline',
    fullIcon: 'mdi-heart',
    halfIcon: 'mdi-heart-half-full',
  }),
};
</script>
