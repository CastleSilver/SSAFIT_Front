<template>
  <div class="footer">
    <v-card-text>
      <v-btn
        v-for="icon in icons"
        :key="icon"
        class="mx-4 white"
        style="margin-left: 10px"
        icon
        @click="share(icon)"
      >
        <v-icon size="30px">{{ icon }}</v-icon>
      </v-btn>
    </v-card-text>
    <v-card-text class="white--text pt-0"
      >SSAFIT 서비스 이용약관 | 개인정보 처리 방침 | 이용약관 | 채용정보<br />
      <br />
      고객센터(이용 및 결제 문의) | cs@SSAFIT.co.kr /02-000-0000 (유료)<br />
      제휴 및 대외 협력 | https://SSAFIT.seoul7.4team/contact <br />
      B2B 이용권 구매 문의 | 싸피마케팅 (ssafit@ssafit.com / 070-0000-0000)
      copyright<br />
      <br />
      주식회사 SSAFIT 서울 7반 4조_허성은_신은정
      <br />
      사업자등록번호 111-11-1111 통신판매업 신고번호 제 2022-서울서초-0965호
    </v-card-text>
    <v-divider></v-divider>
    <v-card-text class="white--text">
      {{ new Date().getFullYear() }} —
      <strong>SSAFIT</strong>
    </v-card-text>
  </div>
</template>
<script>
export default {
  name: "FooterNav",
  data: () => ({
    icons: ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-pinterest"],
    thisUrl: document.URL,
    snsTitle: "운동 영상 관련 커뮤니티 SSAFIT",
    url: "",
  }),
  methods: {
    share(sns) {
      if (sns === "mdi-facebook") {
        this.url =
          "http://www.facebook.com/sharer/sharer.php?u=" +
          encodeURIComponent(this.thisUrl);
        window.open(this.url, "", "width=486, height=286");
      } else if (sns === "mdi-twitter") {
        this.url =
          "http://twitter.com/share?url=" +
          encodeURIComponent(this.thisUrl) +
          "&text=" +
          encodeURIComponent(this.snsTitle);
        window.open(
          this.url,
          "tweetPop",
          "width=486, height=286,scrollbars=yes"
        );
<<<<<<< HEAD
      } else if (sns === "mdi-linkedin") {
        this.url =
          "http://www.linkedin.com/cws/share?url="+
          encodeURIComponent(this.thisUrl); 
        window.open(
          this.url,
          "shareLinkedin",
          "width=400, height=500, resizable=yes"
        );
      } else if (sns === "mdi-pinterest") {
        this.url =
          "http://pinterest.com/pin/create/bookmarklet/?media=MEDIA&url"+
          encodeURIComponent(this.thisUrl);
        window.open(
          this.url,
          "tweetPop",
          "width=486, height=286,scrollbars=yes"
        );
      }
    }
  }
}
=======
      } else if (sns === "band") {
        this.url =
          "http://www.band.us/plugin/share?body=" +
          encodeURIComponent(this.snsTitle) +
          "&route=" +
          encodeURIComponent(this.thisUrl);
        window.open(
          this.url,
          "shareBand",
          "width=400, height=500, resizable=yes"
        );
      }
    },
  },
};
>>>>>>> a24fe73865ee24465a110160857740d7b56586b5
</script>
<style scoped>
.footer {
  background-color: grey;
  color: white;
  text-align: center;
}
</style>
