<template>
  <v-container>
    <!-- <h1 class="display-2 font-weight-bold mb-3">
      My Life
    </h1> -->

    <v-row class="text-center">
      <v-col class="mb-5" cols="12">
        <h2 class="headline font-weight-bold mb-3"></h2>

        <v-timeline>
          <v-timeline-item
            v-for="(item, i) in items"
            :key="i"
            :left="true"
            :fill-dot="true"
            :icon="item.icon"
          >
            <template v-slot:opposite>
              <span v-text="item.yearMonth"></span>
            </template>
            <!-- <v-row> -->
              <!-- <v-col cols="4"></v-col> -->
              <!-- <v-col> -->
                <v-card class="elevation-2">
                  <v-card-title class="headline font-weight-bold">
                    <div v-if="item.url">
                      <a :href="item.url" target="_blank">
                        {{ item.title }}
                      </a>
                    </div>
                    <div v-else>{{ item.title }}</div>
                  </v-card-title>
                  <v-card-text v-if="item.content">{{
                    item.content
                  }}</v-card-text>
                </v-card>
              <!-- </v-col> -->
            <!-- </v-row> -->
          </v-timeline-item>
        </v-timeline>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Main",

  data: () => ({
    items: [
      {
        yearMonth: "2016/4",
        title: "横浜市立大学入学",
        url: "https://www.yokohama-cu.ac.jp/",
        icon: "mdi-school",
        content: "",
      },
      {
        yearMonth: "2017/4",
        title: "株式会社Tagbangers入社（アルバイト）",
        url: "https://www.tagbangers.co.jp/",
        icon: "mdi-office-building",
        content:
          "最初に長期インターン（アルバイト）として働いた会社です。\
エンジニアとして未経験で雇っていただいたので、大きな恩を感じています。\
この会社では、主にWebのフロントエンド開発を行っていましたが、それに限らず、\
バックエンドや機械学習、モバイルアプリ開発のプロジェクトなどにも携わることができ、\
技術への興味を持つきっかけをつくってくれました。",
      },
      {
        yearMonth: "2018/9",
        title: "株式会社Tagbangers退社",
        icon: "mdi-office-building",
      },
      {
        yearMonth: "2019/8",
        title: "株式会社Taktpixel入社（アルバイト）",
        url: "https://taktpixel.co.jp/",
        icon: "mdi-office-building",
        content:
          "現在アルバイトをしているスタートアップです。\
proofrog という、画像同士の比較ができる、印刷業界向けの校正検版ツールを開発しています。\
自分が担当しているのは、主にバックエンドですが、フロントエンドやインフラ周りも必要に応じて担当することがあるので、\
未熟ながらもフルスタックエンジニアのような働きができているのではないかと思います。\
普段は、製品のコアである画像処理関連のアルゴリズムを実装しています。",
      },
      {
        yearMonth: "2020/2",
        title: "株式会社RevComm入社（業務委託）",
        url: "https://www.revcomm.co.jp/",
        icon: "mdi-office-building",
        content:
          "業務委託として参加しました。\
2019年のTech Crunchで優勝した会社なので、人も急速に増えており、かなり成長段階にあると感じました。\
自分が担当したのは主に社内向けのアプリですが、自分が経験したことのない領域も任せてもらえたので、学びが大きかったです。\
特に、インフラ周りの経験はほぼ皆無だったのですが、CI/CDの自動化を任せてもらえたため、クラウド周りの知識をつけることができました。",
      },
      {
        yearMonth: "2020/3",
        title: "横浜市立大学卒業",
        icon: "mdi-school",
      },
      {
        yearMonth: "2020/4",
        title: "横浜市立大学大学院入学",
        url: "https://www.yokohama-cu.ac.jp/ds/",
        icon: "mdi-school",
        content: "",
      },
      {
        yearMonth: "2020/6",
        title: "株式会社RevComm退社",
        icon: "mdi-office-building",
      },
    ],
  }),
};
</script>

<style lang="scss" scoped>
a {
  text-decoration: none;
}
</style>
