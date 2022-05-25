<template>
  <v-app>
    <div>
      <v-app-bar flat style="background-color: #da0037">
        <a href="/" class="ssafit" style="font-family: KickerTrialBlack">
          SSAFIT &nbsp;
        </a>
        <v-spacer></v-spacer>
        <h6 class="mt-3">
          {{ userinfo.nickname }}님 안녕하세요
          <b-icon
            class="profile"
            icon="heart-fill"
            animation="fade"
            font-scale="1"
          ></b-icon>
        </h6>
        <v-menu left bottom>
          <template v-slot:activator="{ on, attrs }">
            <v-btn icon v-bind="attrs" v-on="on">
              <img
                style="border: 2px solid; border-radius: 70%"
                :src="require(`@/assets/images/${userinfo.profile}.png`)"
                width="40px"
              />
            </v-btn>
          </template>

          <v-list>
            <v-list-item
              v-for="(link, idx) in links3"
              :key="idx + 'A'"
              :to="{ path: link.router }"
              class="router"
              link
            >
              <v-list-item-title
                ><img :src="`${link.icon}`" style="width: 30px" />
                {{ link.title }}</v-list-item-title
              >
            </v-list-item>
            <v-list-item @click="userLogout" class="router" link>
              <v-list-item-title
                ><img
                  src="https://img.icons8.com/stickers/100/000000/exit.png"
                  style="width: 30px"
                />
                로그아웃</v-list-item-title
              >
            </v-list-item>
          </v-list>
        </v-menu>
      </v-app-bar>

      <v-main class="main" style="background-color: #da0037">
        <div style="margin: 20px">
          <v-row>
            <v-col cols="2" class="absolute1" style="width: 200px">
              <v-sheet rounded="lg" style="width: 180px">
                <v-list color="transparent">
                  <v-list-item
                    v-for="(link, idx) in links"
                    :key="idx + 'I'"
                    :to="{ path: link.router }"
                    class="router"
                    link
                  >
                    <v-list-item-icon>
                      <img :src="`${link.icon}`" style="width: 40px" />
                    </v-list-item-icon>
                    <v-list-item-content>
                      {{ link.title }}
                    </v-list-item-content>
                  </v-list-item>

                  <v-divider class="my-2"></v-divider>

                  <v-list-item
                    v-for="(link, idx) in links2"
                    :key="idx + 'R'"
                    :to="{ path: link.router }"
                    class="router"
                    link
                  >
                    <v-list-item-icon>
                      <img :src="`${link.icon}`" style="width: 40px" />
                    </v-list-item-icon>
                    <v-list-item-content>
                      {{ link.title }}
                    </v-list-item-content>
                  </v-list-item>
                </v-list>
              </v-sheet>
            </v-col>

            <v-col style="margin-left: 200px">
              <v-sheet min-height="100vh" rounded="lg">
                <router-view />
              </v-sheet>
            </v-col>
          </v-row>
        </div>
      </v-main>
    </div>
  </v-app>
</template>

<script>
import { mapState } from "vuex";

export default {
  data: () => ({
    links: [
      {
        title: "홈",
        router: "/",
        icon: "https://img.icons8.com/stickers/100/000000/home-page.png",
      },
      {
        title: "검색",
        router: "/search",
        icon: "https://img.icons8.com/stickers/100/000000/search.png",
      },
    ],
    links2: [
      {
        title: "찜리스트",
        router: "/vlist/like",
        icon: "https://img.icons8.com/stickers/100/000000/like.png",
      },
      {
        title: "시청기록",
        router: "/vlist/watched",
        icon: "https://img.icons8.com/stickers/100/000000/laptop-play-video.png",
      },
    ],
    links3: [
      {
        title: "프로필 편집",
        router: "/member/check",
        icon: "https://img.icons8.com/stickers/100/000000/edit-user-female.png",
      },
      {
        title: "찜리스트",
        router: "/vlist/like",
        icon: "https://img.icons8.com/stickers/100/000000/like.png",
      },
      {
        title: "시청기록",
        router: "/vlist/watched",
        icon: "https://img.icons8.com/stickers/100/000000/laptop-play-video.png",
      },
    ],
  }),
  computed: {
    ...mapState(["userinfo"]),
  },
  methods: {
    userLogout() {
      this.$store.commit("USER_LOGOUT");
      this.$router.push({ name: "main" });
    },
  },
};
</script>
<style scoped>
.absolute1 {
  position: fixed;
}
.header {
  display: flex;
  justify-content: space-between;
}
.main {
  background-color: grey;
}
.ssafit {
  text-decoration: none;
  color: black;
  margin: 20px 20px;
  padding-top: 30px;
  font-weight: bolder;

  font-size: 60px;
}
.router {
  color: black;
  text-decoration: none;
}
.login {
  color: white;
  font-size: 20px;
}
.v-sheet.rounded-lg {
  background-color: #ededed;
}
.v-toolbar__content {
  height: 10%;
}
.card {
  background-color: black;
}
.mt-3 {
  margin-top: 50px;
  padding-top: 20px;
}
.v-btn--icon {
  margin-top: 25px;
  margin-left: 10px;
  margin-right: 10px;
}
</style>
