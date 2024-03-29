import { Card } from '@fusuma/client';

<!-- sectionTitle: builderscon -->
<!-- note
builderscon
- buildersconは、「知らなかった、を聞く」 をテーマとした技術を愛する全てのギーク達のお祭りです
- 前夜祭を含めると3日間開催された
- 技術の幅が広い
  - ジャンルは何でもあり
- 発表の質が高い
  - プロポーザルを出して選考を通らなければならない

聞いた中で特に面白いと感じたセッションを３つ紹介

目的: 面白そうだから。まずイベントのコンセプトが面白そう。
普段自分の専門領域を深めに勉強会などに行くが、単純に面白そうなことに出会いたいと思った
-->
<Card
  left={<div><img src="../assets/builderscon.png" /></div>}
  right={
    <div>
      <h2>builderscon</h2>
        <ul>
          <li>「知らなかった、を聞く」 技術者の祭典</li>
          <li>前夜祭を含めると3日間開催された</li>
          <li><p>技術の幅が広い</p>
            <ul>
              <li>ジャンルは何でもあり</li>
            </ul>
          </li>
          <li><p>発表の質が高い</p>
            <ul>
              <li>プロポーザルを出して選考を通らなければならない</li>
            </ul>
          </li>
        </ul>
    </div>
  }
/>

---

## 特に面白いと思ったセッション

- [対戦ゲームに学ぶ、フレームワークの設計技法とAIのアルゴリズム入門 *by qsona*](https://builderscon.io/builderscon/tokyo/2019/session/1f34d023-591e-4674-98eb-b2201c8a28be)
- [コンパイラをつくってみよう *by DQNEO*](https://builderscon.io/builderscon/tokyo/2019/session/e6ed1194-9a40-4a8c-92fb-b60f39cd18dd)
- [Oxygen Not Included: Making a Game That Inspires Science	*by Ipsquiggle*](https://builderscon.io/builderscon/tokyo/2019/session/1a239003-960c-11e9-a530-42010af01081)

---
<!-- note
対戦ゲームに学ぶ、フレームワークの設計技法とAIのアルゴリズム入門 by qsona
- 対戦ゲームのルールを定式化
- 定式化するとゲームのAIに活かせる
- boadgame.ioに学ぶフレームワーク設計の勘所
-->
<h2><p>対戦ゲームに学ぶ、</p>フレームワークの設計技法とAIのアルゴリズム入門 by qsona</h2>

- 対戦ゲームのルールを定式化
- 定式化するとゲームのAIに活かせる
- boadgame.ioに学ぶフレームワーク設計の勘所

---

<!-- note
対戦ゲームのルールを定式化
- ターン制のゲームは状態(局面)とMove(指し手)の組み合わせで表現できる
  - 初期状態
  - 終了条件と結果(勝敗)
- ただし、(将棋の場合)ルールが曖昧で完全に定式化できない
  - 「最後の審判」(1997)

将棋だと局面は9x9のマスとコマの配置、持ち駒など
最後の審判: 詰将棋、現行のルールでは勝ち負けが不定となるのが定説とされる

-->

## 対戦ゲームのルールを定式化

- ターン制のゲームは状態(局面)とMove(指し手)の組み合わせで表現できる
  - 初期状態
  - 終了条件と結果(勝敗)
- ただし、(将棋の場合)ルールが曖昧で完全に定式化できない
  - 「最後の審判」(1997)

---

<!-- note
定式化するとゲーム木という木構造で表せる
- 状態(局面)がノード、Move(指し手)が枝
- ゲームの面白さを表せるのではないか
  - 一方的なゲーム(消化試合)
  - 緊張感が持続するゲーム

-->

<Card
  left={
    <div>
      <img src="../assets/game_tree.jpg" />
      <div><span class="reference">引用: https://www.webcyou.com/?p=6997</span></div>
    </div>
  }
  right={
    <div>
      <h3>定式化するとゲーム木で表せる</h3>
        <ul>
          <li>状態(局面)がノード、Move(指し手)が枝</li>
          <li>
            <p>ゲームの面白さを表せるのではないか</p>
            <ul>
              <li>一方的なゲーム(消化試合)</li>
              <li>緊張感が持続するゲーム</li>
            </ul>
          </li>
        </ul>
    </div>
  }
/>

---
<!-- note
一方的なゲーム 消化試合の場合
青が自分。自分がどの手を選んでも最終局面では勝ちを選ぶことができる
-->

<img src="../assets/shouka.png" width="60%" height="60%" />
<br />
<div class="reference">引用: https://speakerdeck.com/qsona/game-model</div>

---

<!-- note
緊張感が持続する持続する試合の場合

最初、一見一番左を選べば勝てる確率が高いが
相手の選択によっては負けを選ぶしかなくなる
この場合右を選ぶといい (勝ちを選べる)
-->

<img src="../assets/atsui.png" width="60%" height="60%" />
<br />
<div class="reference">引用: https://speakerdeck.com/qsona/game-model</div>

---

<!-- note
  - モンテカルロ木探索
    - とりあえず、ゲーム終了まで何回も試行する
    - 勝率が高い手を選ぶ
  - いくつかの戦略を一定の割合で混ぜると強い(例：ポーカーで2割ブラフ)
  - 将棋は完全解析不能なので評価関数が命
  - 
-->

## AIアルゴリズムの話

- モンテカルロ木探索
  - とりあえず、ゲーム終了まで何回も試行する
  - 勝率が高い手を選ぶ
- いくつかの戦略を一定の割合で混ぜると強い
- 将棋は完全解析不能なので評価関数が命

---

<!-- note
- boadgame.ioに学ぶフレームワーク設計の勘所
  - boadgame.io
    - ターン制のゲームを作るためのフレームワーク
    - JavaScript, Node.js, React, TypeScript
-->

## boadgame.ioに学ぶフレームワーク設計の勘所

<img src="../assets/boardgame_io.png" width="60%" height="60%" />

---

<!-- note
主な機能。特筆すべきは状態管理とゲームフェーズ。
  - (将棋) 局面を状態(G)として管理、指し手の履歴もゲームの状態に含まれる
    - 履歴がないと千日手の判定ができない
  - PDS (プレゼンテーションとドメインの分離)
  - 簡易AIの自動生成(モンテカルロ木ベース)
-->

<img src="../assets/boardgame_io_features.png" width="40%" height="40%" />

---

<!--
良いフレームワークとは
- 扱う対象は広いが広すぎない
- 対象の構造を適切に捉えていて頑健性がある
- エコシステムの充実
-->

## 良いフレームワークとは
- 扱う対象は広いが広すぎない
- 対象の構造を適切に捉えていて頑健性がある
- エコシステムの充実

---

<!-- note
コンパイラをつくってみよう by DQNEO
- ライブコーディング形式のセッション
    - 実際は会場全体でモブプロ状態だった
- 式を入力として演算結果の数値を主力するコンパイラ
  - 例: '30 + 12' -> 42
- ソースコードを標準入力で受け取って、アセンブリを標準出力に吐く
- フルスクラッチでコンパイラを作るところライブコーディング
-->

## コンパイラをつくってみよう by DQNEO

- ライブコーディング形式のセッション
- 式を入力として演算結果の数値を主力するコンパイラ
  - 例: '30 + 12' -> 42
- ソースコードを標準入力で受け取って、アセンブリを標準出力に吐く

---

<!-- note
30をraxレジスタに書き込む
12をrcxレジスタに書き込む
raxレジスタとrcxレジスタを加算する
-->

<img src="../assets/compiler1.png" width="60%" height="60%" />
<br />
<div class="reference">引用: https://speakerdeck.com/dqneo/how-to-make-a-compiler</div>

---

<p>スライドによる解説とライブコーディングが織り交ぜられて</p>
わかりやすいセッションだった

---

<img src="../assets/compiler2.png" width="60%" height="60%" />
<br />
<div class="reference">引用: https://speakerdeck.com/dqneo/how-to-make-a-compiler</div>

---

<img src="../assets/compiler3.png" width="60%" height="60%" />
<br />
<div class="reference">引用: https://speakerdeck.com/dqneo/how-to-make-a-compiler</div>

---

<img src="../assets/compiler4.png" width="60%" height="60%" />
<br />
<div class="reference">引用: https://speakerdeck.com/dqneo/how-to-make-a-compiler</div>

---

<img src="../assets/compiler5.png" width="60%" height="60%" />
<br />
<div class="reference">引用: https://speakerdeck.com/dqneo/how-to-make-a-compiler</div>

---

<img src="../assets/compiler6.png" width="60%" height="60%" />
<br />
<div class="reference">引用: https://speakerdeck.com/dqneo/how-to-make-a-compiler</div>

---

<!-- note
- 言語はなんでもよい
- コンパイラをつくりはじめるのに特殊な知識はいらない
- 作りながら学ぶというやり方がおすすめ
- 今ならchibiccを写経するのがいい
-->

- 言語はなんでもよい
- コンパイラをつくりはじめるのに特殊な知識はいらない
- 作りながら学ぶというやり方がおすすめ
- 今ならchibiccを写経するのがいい

---

<!-- note
Oxygen Not Included: Making a Game That Inspires Science by Ipsquiggle

- 物理学や科学のルールを持ち込んだシミュレーションゲーム
- 街づくり + サバイバルがコンセプト(シムシティに代表されるジャンル)
- の開発者が登壇
- ちなみに発表は同時通訳付きだった (同時通訳スポンサーに感謝)

ONIは基本、横方向から見たマップ上で上下に穴を掘りつつ、
食料を作ったり、施設をたてたりして、
それらを使って生き延びていくことを延々と続けるゲームです。
-->


<Card
  left={<div><img src="https://miro.medium.com/max/3840/1*weLorZCUrWYHNsZaZdS0EA.jpeg" /></div>}
  right={
    <div>
      <h3>Oxygen Not Included (通称ONI)</h3>
        <ul>
          <li>物理学や科学のルールを持ち込んだシミュレーションゲーム</li>
          <li>街づくり + サバイバルがコンセプト(例: シムシティ)</li>
          <li>の開発者が登壇</li>
          <li>ちなみに発表は同時通訳付きだった</li>
        </ul>
    </div>
  }
/>

---

<!-- note
- 重力
- 熱伝導
- 状態変化(気体、液体、個体)
- 疾病、ウィルス

例えば気体にも重力が作用する
水素 < 酸素 < 天然ガス < 塩素 < 二酸化炭素
全てのオブジェクトに熱伝導率が設定されていて
発電機の熱が空気を伝わって全体の気温を上げる
-->

<Card
  left={
    <div>
      <img src="../assets/oni_gravity.png" />
      <div><span class="reference">引用: https://medium.com/schematics-not-included/what-makes-oxygen-not-included-special-d52c280205b3</span></div>
    </div>
  }
  right={
    <div>
      <h3>様々な科学的要素が複雑に作用する</h3>
        <ul>
          <li>重力</li>
          <li>熱伝導</li>
          <li>状態変化(気体、液体、個体)</li>
          <li>流体力学</li>
          <li>疾病、ウィルス</li>
          <li>...</li>
        </ul>
    </div>
  }
/>

---

<!-- note
ONIの難しさ・醍醐味 (=副作用)

- 基本的に全ての行為には副作用が発生する
  - 例: 火力発電には二酸化炭素と熱が発生する
- 副作用を解決するために試行錯誤
  - 仮説 -> 実験 -> 考察 の繰り返し

プログラミングにも通づる面白さがある

-->

## ONIの難しさ・醍醐味 (=副作用)

- 基本的に全ての行為には副作用が発生する
  - 例: 火力発電には**二酸化炭素**と**熱**が発生する
- 副作用を解決するために試行錯誤
  - 仮説 → 実験 → 考察 の繰り返し

---

## ゲームを通して自然と科学的思考が身につく

プログラミングに通づる面白さがある

---

<!-- note
ほかにも面白い(面白そうだった)発表がたくさんあった
- PHPでJVMをつくった人
- 自動作曲入門
- Kyash, メルペイのアーキテクチャ
- スーパーカミオカンデの開発裏話
- webpack / Babelがどう動いているか解説
-->

### ほかにも面白い(面白そうだった)発表がたくさんあった
- PHPでJVMをつくった人
- 自動作曲入門
- Kyash, メルペイのアーキテクチャ
- スーパーカミオカンデの開発裏話
- webpack / Babelがどう動いているか解説

---

<!-- note
豪華なディナー (スポンサーに感謝)
-->

<img src="../assets/breakfast.jpg" width="40%" height="40%" />

---

<!-- note
最後にbuildersconで一番心に残った言葉で締める
コンパイラを作ろうセッションの質問タイムにて
Q. コンパイラを作るモチベーションの維持はどうしたのか？
A. コンパイラ作りが終わるまで他のことはやらないと決めた
   作り終わらなかったら何も成し遂げられないまま一生を遂げてしまう
面白いもの新しく興味が出たものがたくさん見つかったけど、まずはアプリ制作がんばろうと思う
-->

#### Q. コンパイラを作るモチベーションの維持はどうしたのか？

---

<!-- note
最後にbuildersconで一番心に残った言葉で締める
コンパイラを作ろうセッションの質問タイムにて
Q. コンパイラを作るモチベーションの維持はどうしたのか？
A. コンパイラ作りが終わるまで他のことはやらないと決めた
   作り終わらなかったら何も成し遂げられないまま一生を遂げてしまう
面白いもの新しく興味が出たものがたくさん見つかったけど、まずはアプリ制作がんばろうと思う
-->

#### Q. コンパイラを作るモチベーションの維持はどうしたのか？
### A. コンパイラ作り終わるまで他のことはやらないと決めた

