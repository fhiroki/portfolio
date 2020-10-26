<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="mb-5" cols="12">
        <h2 class="headline font-weight-bold mb-3"></h2>

        <v-timeline>
          <v-timeline-item
            v-for="(item, i) in items"
            :key="i"
            :left="item.side == 'right' ? false : true"
            :fill-dot="true"
            :color="item.color"
            :icon="item.icon"
          >
            <template v-slot:opposite>
              <span
                :class="`headline font-weight-bold ${item.color}--text`"
                v-text="item.yearMonth"
              ></span>
            </template>

            <v-card class="elevation-2">
              <v-card-title
                :class="`headline font-weight-bold ${item.color}--text`"
              >
                <div>{{ item.title }}</div>
              </v-card-title>

              <v-card-text v-if="item.content || item.works" class="card-text">
                <div v-html="item.content"></div>

                <v-expansion-panels popout class="expansion-panel">
                  <v-expansion-panel v-for="(work, i) in item.works" :key="i">
                    <v-expansion-panel-header>
                      <v-row no-gutters>
                        <v-col cols="5" style="padding-top: 5px">
                          {{ work.title }}
                        </v-col>
                        <v-col cols="3">
                          <v-icon>mdi-code-tags</v-icon>
                          <span v-for="(language, i) in work.languages" :key="i">
                            <v-icon small>mdi-language-{{ language }}</v-icon>
                          </span>
                        </v-col>
                        <v-col cols="4">
                          <v-icon>mdi-calendar</v-icon>
                          {{ work.period }}
                        </v-col>
                      </v-row>
                    </v-expansion-panel-header>

                    <v-expansion-panel-content>
                      <div v-html="work.content"></div>
                    </v-expansion-panel-content>
                  </v-expansion-panel>
                </v-expansion-panels>
              </v-card-text>
            </v-card>
          </v-timeline-item>
        </v-timeline>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Home",

  data: () => ({
    items: [
      {
        yearMonth: "2016/4",
        title: "横浜市立大学入学",
        icon: "mdi-school",
        color: "light-green",
        works: [
          {
            title: "卒業研究",
            period: "大学3〜4年",
            languages: ["python"],
            content: `卒業研究として、\
<a href="https://github.com/fhiroki/analyze-leed-pattern" target="_blank" rel="noopener noreferrer">画像認識ソフト</a>\
を開発しました。このプロジェクトは、実験の効率化を図るもので、\
LEEDと呼ばれる電子回折装置を用いて撮影された画像から、\
回折スポットを自動で検出し、解析を行います。\
Python で CLI ツールとして実装しており、画像の解析には OpenCV を使用しました。\
このプロジェクトでは機械学習は用いていませんが、\
クラシカルな画像処理でも精度の高い検出結果を得ることができました。`,
          },
        ],
      },
      {
        yearMonth: "2017/4",
        title: "株式会社Tagbangers入社（アルバイト）",
        icon: "mdi-office-building",
        color: "red",
        content:
          "最初に長期インターン（アルバイト）として働いた会社です。\
エンジニアとして未経験で雇っていただいたので、大きな恩を感じています。\
この会社では、主にWebのフロントエンド開発を行っていましたが、それに限らず、\
バックエンドや機械学習、モバイルアプリ開発のプロジェクトなどにも携わることができ、\
技術への興味を持つきっかけをつくってくれました。",
        works: [
          {
            title: "社内研修",
            period: "0〜3ヶ月",
            languages: ["java"],
            content:
              "会社に入ってから約３ヶ月間は、研修期間として、様々な課題にチャレンジしました。\
タグバンガーズはWeb開発が中心の会社で、主な言語としてはJava、フレームワークはSpringを使用しているので、まずは、Javaで課題を出していただきました。\
具体的には、\
<ol>\
<li>誕生日から年齢を出力するプログラム（Java）</li>\
<li>四則演算ができる電卓（JavaScript）</li>\
<li>catコマンド（Java）</li>\
<li>lsコマンド・latrのオプションつき（Java）</li>\
<li>chatアプリ（Java）</li>\
<li>Webサーバ（Java）</li>\
</ol>\
の順で課題に挑戦しました。\
これらの課題はそれぞれに核となる技術があり、それらについての理解を深めるという目的で、社長自らが考えてくださいました。\
当時はプログラムをほぼ書いたことがなかったので、どの課題にも苦戦しながら臨みましたが、\
わからないところがあったら、丁寧に、楽しそうに教えてくれたので、こちらも楽しんで学べました。\
また、少し難易度の高いテーマについては、社内勉強会と称して、忙しい中時間をとって説明してくれたりもしました。\
分かりやすいというのはもちろんですが、全体的に楽しそうに教えてくれたのが印象的でした。\
そうして少しずつプログラムに対する理解を深めていき、約3ヶ月後からはいよいよ実務に入らせていただくことになりました。",
          },
          {
            title: "iOSアプリの保守、開発",
            period: "3〜6ヶ月",
            languages: ["swift"],
            content:
              "約３ヶ月経った頃には、先輩のエンジニアにご指導いただきながら、iOSアプリの保守や開発を行いました。\
ここでは、現場でどのようなツールを使い、どのように仕事を進めていくのかを学ぶことができました。\
具体的には、Gitの使い方・レビューの受け方・タスク管理の仕方・データベースの扱い方などです。\
実際の開発現場を知れたというのは、かなり価値のあることだと思っています。\
なぜなら、例えプログラムが学べる学校に通っていたとしても、開発手法については学べないと思うからです。\
業務内容としては、既存アプリのバグ修正が中心でした。\
学んだことは、バグを１つ潰すのにも膨大な時間がかかり、論理的に考えていかないといけないということでした。\
一見当たり前のことのようにも思えますが、実際にやってみるまではデバッグの大変さを理解していなかったので、大きな学びの１つだと思います。",
          },
          {
            title: "スマホアプリの開発",
            period: "6〜10ヶ月",
            languages: ["javascript"],
            content:
              "NativeScriptという、iOSとAndroidの両方を同時に開発できるフレームワークを用いて、スマホアプリの開発を行いました。\
まず画面のモックアップを作り、その後でAPIコール部分を作りました。\
このアプリは、業務用の、比較的簡単な操作しか行わないものだったので、求められる技術レベルはさほど高くなかったように思えます。\
しかし、レイアウト調整や土台作りを除き、モックアップからストアでの配布までほとんど１人で作らせていただけたので、\
責任感もそうですが、達成感がかなり大きかったです。\
また、従来はiOSとAndroidで別々にコードを書かないといけないところ、\
１つのコードで実現できてしまうクロスプラットフォームも魅力的でした。\
ここで学んだのは、アプリを作る上で大変なのは、最後の１手間だということです。\
モックアップを作るときは、実際に画面ができていくので、進捗も分かりやすく、達成感も感じやすいです。\
しかし、最後は完璧な状態にしないといけないので、細かいレイアウトの調整やエラー制御などが求められます。\
これらの１手間がかなり厳しく、色々な手直しが入り、正直心が折れそうになりました。その分、リリースが完了した時の達成感は一入でした。",
          },
          {
            title: "Spring One参加",
            period: "8ヶ月頃",
            languages: ["java"],
            content:
              "インターンを始めて約半年が経った頃、社内研修としてSpring Oneに参加するため、サンフランシスコに連れていってもらいました。\
海外に行くのは生まれて初めてだったので、非常に貴重な経験をさせてもらったと思っています。\
海外に行って一番驚いたのは、外人のフレンドリー具合が日本人の比ではないということです。\
カンファレンスの登壇者で有名な人に、そうとは知らず声をかけてみたら、サンフランシスコを巡るミニツアーを開催してくれました。\
僕は英語もまともに話せないのに、優しくしてくれて、さらに名所の紹介までしてくれるなんて、日本人の感覚からは理解ができません。\
それほどフレンドリーで、紳士な人がこの世にいるということは、衝撃的でした。\
また、もう１つの大きな変化としては、海外に行ったことで、日本が好きになったことです。\
海外に行くまでは、日本は他の国に比べてそこまでいい国だと思っていませんでした。\
しかし、サンフランシスコの物価が高いというのもあるとは思いますが、全体的に日本のサービスの質の方が高く感じられました。\
特に、日本の食べ物（特に味噌汁）が恋しくなった時に、日本も捨てたもんじゃないと思えました。\
「おもてなし」の精神は口だけではなく、本当なんだと実感しました。",
          },
          {
            title: "Webアプリ、APIの開発",
            period: "10〜12ヶ月",
            languages: ["java", "javascript"],
            content:
              "WebアプリはAngularというJavaScriptのフレームワーク、APIはSpringで実装しました。\
AngularはNativeScriptでも使っていたので、比較的習得が早かった気がします。\
Springを本格的に触ったのはこれが初めてで、それもSpring Data RESTという特殊な部類だったので、なかなかに苦戦しました。\
しかし、RESTでAPIを作ると、簡単にエンドポイントが作れてしまうので、メリットも大きいように思えました。\
Springに関しては奥が深く、まだまだ勉強すべきことがたくさんあるので、今後の学習課題の１つだと思っています。",
          },
          {
            title: "画像認識アプリの開発",
            period: "12〜15ヶ月",
            languages: ["python"],
            content:
              "機械学習のライブラリを用いた画像認識の組み込みアプリを開発しました。\
前々から機械学習には興味があったので、このプロジェクトが決まった時は嬉しかったです。\
ただ、機械学習に興味があっただけで、具体的に何かを作ったことはなかったので、ここで実際に作らせていただけたのは大きかったです。\
このプロジェクトを契機に、より機械学習に関する知識を深めたいと思い、自ら学習するようにもなりました。\
その中でも、Coursera の Machine Learning の講義は大変勉強になりました。",
          },
          {
            title: "Webアプリの開発",
            period: "15〜18ヶ月",
            languages: ["javascript", "css3"],
            content:
              "最後のプロジェクトに臨む頃には、Gitの使い方やタスク管理の仕方などがある程度習熟してきて、基本的な操作は問題なく行えるようになりました。\
正直にいうと、最初の頃はあまり理解せずに、GUI頼みでそれらのツールを使っており、だいぶ経ってからきちんと理解するに至りました。\
月並みですが、やはり基礎は大切で、最初の段階できちんと理解しておくべきだと、振り返って感じました。\
このプロジェクトでは、主にレイアウトに関する学びが大きかったと思います。\
これまで直接CSSを触る機会はあまりなかったのですが、触れてみると意外にも奥深く、デザインをいじるのも楽しいと感じました。",
          },
        ],
      },
      {
        yearMonth: "2018/9",
        title: "株式会社Tagbangers退社",
        icon: "mdi-office-building",
        color: "red",
        side: "right",
      },
      {
        yearMonth: "2019/8",
        title: "株式会社Taktpixel入社（アルバイト）",
        icon: "mdi-office-building",
        color: "blue",
        content: `現在アルバイトをしているスタートアップです。\
<a href="https://proofrog.cloud/" target="_blank" rel="noopener noreferrer">proofrog</a>という、画像同士の比較ができる、\
印刷業界向けの校正検版ツールを開発しています。\
自分が担当しているのは、主にバックエンドですが、フロントエンドも必要に応じて担当することがあるので、\
未熟ながらもフルスタックエンジニアのような働きができているのではないかと思います。\
普段は、製品のコアである画像処理関連のアルゴリズムを実装しています。`,
      },
      {
        yearMonth: "2019/12（2日間）",
        title: "株式会社サイバーエージェントインターン",
        icon: "mdi-office-building",
        color: "green",
        content:
          "「CA Tech Challenge Web Frontend Challenge Vol.2」 という２日間のイベントで、\
漫画ビュワーを作成しました。従来の漫画ビュワーにはないような、回転機能を実装することで、\
オリジリナリティを発揮しました。",
      },
      {
        yearMonth: "2020/2",
        title: "株式会社RevComm入社（業務委託）",
        icon: "mdi-office-building",
        color: "light-blue",
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
        color: "light-green",
        side: "right",
      },
      {
        yearMonth: "2020/4",
        title: "横浜市立大学大学院入学",
        icon: "mdi-school",
        color: "light-green",
        content:
          "機械学習関連の勉強がしたかったので、データサイエンス研究科に入学しました。\
          CS系大学院と迷いましたが、卒業する年にちょうど新たな研究科が設立されたので、運命を感じ、\
          そのまま横浜市立大学の大学院へ進学しました。",
      },
      {
        yearMonth: "2020/6",
        title: "株式会社RevComm退社",
        icon: "mdi-office-building",
        color: "light-blue",
        side: "right",
      },
      {
        yearMonth: "2020/9（2週間）",
        title: "楽天株式会社インターン",
        icon: "mdi-office-building",
        color: "red",
        content:
          "2週間のインターンシップで「オンラインで人と人を繋ぐ」をテーマにプロダクトを開発しました。\
6人のチームで、自分はテックリードを担当しました。あまり経験のないモバイル開発でしたが、\
FlutterとFirebaseを使って大学生のためのチャットアプリを開発しました。\
主な機能は、受講している授業で友達を探すことができ、チャットができるというものです。\
タイムライン機能なども盛り込むことにより、より気軽にトークができるような設計にしました。",
      },
    ],
  }),
};
</script>

<style lang="scss" scoped>
a {
  text-decoration: none;
}
.card-text {
  text-align: left;
}
.expansion-panel {
  padding-top: 10px;
  i {
    margin-bottom: 3px;
  }
}
</style>
