#化学反応ネットワーク設計ツールの拡張

【はじめに】

PEN toolboxに加えて捕食反応(Predator Prey=PP)も使用できる化学反応ネットワーク設計・シミュレーションシステムを実装した。化学反応ネットワークは分子群ロボットのコントローラの設計に使われる。


【研究背景】

先行研究としてPENのみのシミュレーション(Aubert et al., 2014 )やPEN＋PPの常微分方程式構築（Aubert-Kato, Cazenille, 2020)があったが、PEN+PPを使ってかつ、中間反応体の自動生成から常微分方程式に基づいたシミュレーションまで行うツールは今まで実装されていなかった。

<img width="360" alt="スクリーンショット 2022-11-14 0 20 08" src="https://user-images.githubusercontent.com/93179388/201529358-c1b8e6e1-8688-47f3-8db3-ec66e280be98.png">

【目的】

シミュレーションツールを開発している目的はWetな実験のデメリット(時間、費用）を補うためである。
このシミュレーションシステムのメリットとしてはユーザーが化学反応ネットワークを入力しただけで簡単に、二つの反応タイプ(PEN,PP)に応じた反応中間体の生成から、微分方程式に基づいたシミュレーションまで行うことができる。すべてのコードはPythonで作成した。
プログラミングの知識が殆どなくてもPEN＋PPを使ったシミュレーションを行うことができる。

【方法】

PPシステムやPEN toolboxに基づく抽象的な化学反応ネットワークを入力として受け取り、自動的に常微分方程式に組み込み、中間反応体を含めた全ての反応を自動的にシミュレーションさせた。
<img width="423" alt="スクリーンショット 2022-11-14 0 22 38" src="https://user-images.githubusercontent.com/93179388/201529490-0b30c8cb-2082-4c3f-8230-9ab457ce4d6e.png">

【検証】

今回Oligater(Montagne et al., 2011)とBistable　Switch(Fauste-Gay et al., 2022)のモデルを化学反応ネットワークとして入力した。
実行結果は以下の通りだ。

・Oligater　→三つのPEN反応で構成
1つの分子(青)が自己触媒反応で濃度を増やして、もう１つの分子（オレンジ)を増やす。また、オレンジが抑制分子を増やして、青の触媒反応を抑制する。
参考文献と同じく、テンプレート分子の濃度により、安定性、減衰振動、振動を確認できた。

<img width="435" alt="スクリーンショット 2022-11-14 0 00 26" src="https://user-images.githubusercontent.com/93179388/201528408-24f08d9f-f266-4a41-84e7-ec7a9abb9782.png">


・Bistable Switch(双安定性スイッチ）→PEN+PP反応で構成
Nが自己触媒反応で濃度を増やすが、同時にP2が捕食して抑制分子のP1を増やす。
NとP2の初期濃度により、Nが二つの安定状態になる可能性を確認できた。
<img width="523" alt="Bistable" src="https://user-images.githubusercontent.com/93179388/201527889-b656225d-18f0-4e7a-963c-d90d3c071be7.png">

【まとめ・今後】
・本研究ではPEN toolboxに加えてPredator Prey System(PP)も使用できる化学反応ネットワーク設計・シミュレーションシステムを実装した。
・今回参考にしたOligatorとBistable Switchの論文の結果と本研究の振る舞いは似てるがパラメーターが異なるため、更なる改善が必要
・現在は手作業で化学反応ネットワークを入力しているが、今後、自動変換関数を開発する。
・より実験の環境に近づけるため、「揺らぎ」の影響や確率論的な個体差もノイズとして取り入れたい。


