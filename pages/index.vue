<template>

  <v-app>
    <v-form>
      <v-container>
        <v-row>
          <v-col
            cols="12"
          >
            <v-text-field
              v-model="name"
              label="Name"
            ></v-text-field>
          </v-col>
          </v-row>
          <v-row>
            <v-col
            cols="12"
            md="6"
          >
            <v-text-field
              v-model="email"
              label="E-mail"
            ></v-text-field>
          </v-col>
          </v-row>
          <v-row>
          <v-col
          class="d-flex"
          cols="12"
          sm="4"
        >
          <v-select
            :items="items"
            label="select"
          ></v-select>
        </v-col>
        </v-row>
        <v-row>
            <v-col
              cols="6"
              sm="2"
              md="2"
            >
              <v-checkbox
                v-model="ex4"
                label="red"
                color="red"
                value="red"
                hide-details
              ></v-checkbox>
            </v-col>
            <v-col
              cols="12"
              sm="2"
              md="2"
            >
              <v-checkbox
                v-model="ex4"
                label="indigo"
                color="indigo"
                value="indigo"
                hide-details
              ></v-checkbox>
            </v-col>
            <v-col
              cols="12"
              sm="2"
              md="2"
            >
              <v-checkbox
                v-model="itemColors"
                label="orange"
                color="orange"
                value="orange"
                hide-details
              ></v-checkbox>
            </v-col>
          </v-row>
          <v-radio-group
        v-model="row"
        row mandatory
      >
        <v-radio
          label="男"
          value="1"
        ></v-radio>
        <v-radio
          label="女"
          value="2"
        ></v-radio>
      </v-radio-group>
      <v-btn color="primary">
      ボタン
    </v-btn>
      </v-container>
    </v-form>
  </v-app>

</template>

<script>
  import axiosBase from "axios"
  import { mdiCardAccountDetails, mdiFruitPineapple } from '@mdi/js'

  const axios = axiosBase.create({
    baseURL: '/api',
    headers: {
      'Content-Type': 'application/json',
      'X-Requested-With': 'XMLHttpRequest'
    },
    responseType: 'json'
  })

  export default {
    components: {},
    data() {
      return {
        isLoggedIn: false,
        userId: null,
        profile: null,
        contact: {
            name: '',
            gender: null,
            mail: '',
            type: '',
            body: '',
            route: []
        },
        name: '',
        email: '',
        items: ['', 'Foo', 'Bar', 'Fizz', 'Buzz'],
        itemColors: ['red', 'indigo', 'orange'],
        ex4: ['red', 'indigo', 'orange'],
        row: null,
        mdiCardAccountDetails,
        mdiFruitPineapple
      }
    },
    async mounted() {
      this.userId = 'abc'
      this.isLoggedIn = true
    },
    methods: {
    }
  }
  </script>
  <style scoped lang="scss">
  .app-wrapper {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    background-color: #3ee577;
  }
  .header {
    margin: 8px 0 0 0;
    h2 {
      margin: 8px 0 0 0;
      font-size: 18px;
      color: #ffffff;
    }
  }
  .member-card-app {
    display: flex;
    flex-direction: column;
    height: 100%;
    width: 100%;

    .member-card {
      margin: 12px 20px 0 12px;
      padding: 12px 0 24px;
    }
  }
  .qr-code-app {
    display: flex;
    justify-content: center;
    .qr-code-wrapper {
      position: relative;
      .qr-code {
        max-width: 240px;
        width: 100%;
      }
      .app-icon-wrapper {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        .white-circle {
          width: 60px;
          height: 60px;
          border-radius: 30px;
          background-color: #ffffff;
          .avatar {
            margin: 3px;
          }
        }
        .app-icon {
          max-width: 54px
        }
      }
    }
  }
  </style>
