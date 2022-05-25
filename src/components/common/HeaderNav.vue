<template>
  <v-app>
    <div>
      <v-app-bar app flat style="background-color: #DA0037">
        <a href="/" class="ssafit" style="font-family: KickerTrialBlack"> SSAFIT &nbsp;</a>

        <v-spacer></v-spacer>
        <v-btn to="/user/login" color="black" class="login"> Log In </v-btn>
      </v-app-bar>

      <v-main class="main" style="background-color: #DA0037">
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
  }),
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
  margin-top: 25px;
  color: white;
  font-size: 20px;
}
</style>
