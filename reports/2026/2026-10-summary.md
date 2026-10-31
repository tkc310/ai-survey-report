# 月次 AI 調査サマリー 2026-10

対象: 2026-10-01〜10-31（JST）。読んだもの: [2026-10-16](2026-10-16.md)、[2026-10-17](2026-10-17.md)、[2026-10-24](2026-10-24.md)、[2026-10-31](2026-10-31.md)、[logs/feedback.md](../../logs/feedback.md)、[logs/runs/](../../logs/runs/)。週次とログは書き換えていない。設定とスキルも変えていない。

価格は 100 万トークンあたりの入力/出力（USD）。表の各セルは「1位 / 2位 / 3位」。

確認できなかったこと:

- 10/1〜10/8 を覆う週次はリポジトリに無い。比較の起点は最初の週次である 2026-10-16（対象期間は 10/9〜10/16）。
- `logs/runs/` にあるのは手順の README だけで、10月の `YYYY-MM-DD.md` は無い。実行ごとの判断は確認できなかった。
- 週次4本の推奨表に、枠ごとの推奨エフォートは無い。
- 複雑なコーディングの Claude 限定は、単一の性能順にできなかった。オーケストレーションとコーディングの Claude 3位も、性能値だけでは決まらなかった。
- 2026-10-24 が出典にした Yahoo!ニュースの URL は、今回開くと 404 だった。

外部リンクは、このファイルを書いた 2026-10-31 に開き直したものだけを出典にした。

## 1. 作業別おすすめモデル

### 1.1 月内の変化

#### 起点（2026-10-16）

| 作業 | フラッグシップ | 妥当なコスパ | Claude 限定 |
| --- | --- | --- | --- |
| 文章作成・判断 | Claude Opus 5.5 / Gemini 4 Argon / GPT-6 Astra | Claude Sonnet 5.5 / GPT-6.1 Sol / Grok 4.7 | Opus 5.5 / Fable 5.1 / Sonnet 5.5 |
| コーディング | Claude Opus 5.5 / Grok 4.7 / GPT-6 Astra | Grok 4.7 / GPT-6.1 Sol / Claude Sonnet 5.5 | Sonnet 5.5 / Opus 5.5 / Haiku 5.5 |
| 複雑なコーディング | Claude Opus 5.5 / Gemini 4 Argon / GPT-6 Astra | Gemini 4 Argon（導入価格） / Grok 4.7 / GPT-6.1 Sol | Opus 5.5 / Fable 5.1 / Sonnet 5.5 |
| レビュー | Claude Opus 5.5 / GPT-6 Astra / Gemini 4 Argon | Claude Sonnet 5.5 / GPT-6.1 Sol / Grok 4.7 | Opus 5.5 / Sonnet 5.5 / Fable 5.1 |
| オーケストレーション | Claude Opus 5.5 / GPT-6 Astra / Gemini 4 Argon | GPT-6.1 Sol / Claude Sonnet 5.5 / Grok 4.7 | Opus 5.5 / Sonnet 5.5 / Haiku 5.5（サブエージェント） |

この号に推奨エフォートは無い。Claude 列はコストを見た並びになっている（後述）。

#### 2026-10-17: 順位の入れ替えは無い

表のセルは 10-16 と同じ。本文が強調した点は次の二つ。

- Gemini 4 Argon の一般提供（10/13）。導入価格 $2/$10 は 11/30 まで。[G1][G2]
  本文は「コスパ枠の2位に推奨」と書く。表では複雑なコーディングのコスパ1位が Argon のままで、10-16 からセルは動いていない。
- Claude Sonnet 5.5 の Terminal-Bench 4.0 70.6% を表中最高と明記。キャッシュ読み取りは半額。[A3][A4]
  同じ 70.6% は 10-16 にも「Haiku 5.5 発表時の参考値」としてある。順位は変わっていない。

数値の揺れ: GPT-6 Astra の Terminal-Bench 4.0 が 57.9%（10-16）から 57.7%（10-17）になっている。出典はどちらも [A1]。理由は本文に無い。10-24 以降は 57.9% に戻る。

#### 2026-10-24: 複雑なコーディングのフラッグシップ3位

入れ替えは1件。

- 複雑なコーディングのフラッグシップ3位を、GPT-6 Astra から Muse Wonder に変えた。
  理由: DeepSWE 1.1 は 78.8、SWE-Marathon は 53.1（Opus は 74.2 / 46.3、Astra は 74.1 / 42.5）。API は $4/$20、コンテキストは 1M。超長期のリポジトリ作業で公式比較表の首位級。[M1][M2][A1]
  Muse Wonder Full（DeepSWE 79.0、SWE-Marathon 57.5）は Muse Code の Power $50 / Maximum $200 限定で、トークン課金の表には入れていない。

その他の順位は不変。エフォートの指定も無い。根拠に努力条件が足されたのは次の1点。

- GPT-6.1 Sol のオーケストレーション: AutomationBench では medium effort で Opus を 2.2 ポイント上回ると公式が主張。[O4]
  コスパ1位は Sol のまま（10-31 に Terra へ変わる）。

順位以外で、あとから表の読み方が変わる記録:

- Sonnet 5.5 の GDPval-AA を 1840 から 1844 に更新。[A4]
  10-31 は、Haiku の発表ページにある参照列が 1840、Sonnet 自身の表が 1844 なので 1844 を使う、と書いている。[A3][A4]
- GPT-6.1 Sol のキャッシュ入力は、公式発表と料金表とも $0.10 で一致。[O1][O4]
  10-16 と 10-17 の「$0.10 または $0.20」は、GPT-6 Sol 本体の $0.20 との混同だった、と 10-24 が説明している。

#### 2026-10-31: Terra をコスパ枠へ、Carbon は対象外

入れ替えは次の二つ。どちらも GPT-6.1 Terra（10/26）による。[O1][O7][O8]

- 文章作成・判断のコスパ3位を、Grok 4.7 から GPT-6.1 Terra に変えた。
  Terra は $1/$5、キャッシュ入力 $0.05、コンテキスト 1,050,000。最大努力の内部誤り率 4.3% は Astra / Sol に近い。GDPval の公表値が無いので3位。Grok 4.7 は $2/$6（200K トークン未満）で Terra より高い。[O7][X1]
  入力が 272K を超えると、リクエスト全体が入力2倍・出力1.5倍。
- オーケストレーションのコスパを、GPT-6.1 Sol / Claude Sonnet 5.5 / Grok 4.7 から、GPT-6.1 Terra / GPT-6.1 Sol / Claude Sonnet 5.5 に変えた。Grok 4.7 はこの枠から外れた。
  理由: Agents’ Last Exam の中程度の努力で Astra と同等、トークン単価は約 1/10。最大努力では Opus 5.5 よりトークン効率が3倍超、トークン単価は 1/4 で、タスク単価は約9倍安い。Astra と Sol の3倍以上速い。$1/$5。[O7][O8]
  Grok 4.7 は、コンピュータ操作の公表スコアが Terra / Sol / Sonnet に負け、単価も Terra より高い。[X1][O7]

動かなかった枠:

- フラッグシップは、複雑なコーディング以外、10-16 から同じ。複雑なコーディングは 10-24 の Opus 5.5 / Argon / Muse Wonder のまま。
- コーディングとレビューのコスパは、10-16 から同じ。
- Claude 列の週次上の並びも、10-16 から同じ。コストを外した組み直しは、この月次の 1.2 で行う。週次自体は組み直していない。

検討して表に入れなかったもの:

- Gemini 4 Carbon（10/28）。Google は AA Intelligence Index v5 で 59、1位と発表。提供はサイバー防御の一部と Fairwind の信頼パートナーに限られ、開発者 API は未公開。導入価格は Argon と同じ $2/$10（その後 $4/$20）。複雑なコーディングのフラッグシップは据え置き。[G4]
- Mistral Large 4。API は $0.70/$2.10。公式の Terminal-Bench 4.0 は 41%。Hugging Face の紹介は同じベンチを 28.3% とも書いており、条件の差は週次の時点でわからない。どちらの値でもコーディングの上位3モデルに届かない。[M4][M5]
- GPT-6.1 Terra のコーディング枠。Terminal-Bench 4.0 は最大努力で 50.3%。公式は難しいコーディングに Sol と Astra を残している。[O7]
- Terra のレビュー枠。コード差分向けの公式ベンチが無く、Terminal-Bench は 50.3%。[O7]

オーケストレーションのフラッグシップは、10-16 から Opus 5.5 / GPT-6 Astra / Argon のまま。AutomationBench は Astra の 41.4% が Opus の 40.0% より高い、と各号が書きながら、1位は入れ替えていない。入れ替えない理由は週次に無い。

Argon の導入価格 $2/$10 は 11/30 まで。12/1 から $4/$20。[G1][G2]

推奨エフォートの指定は、10-31 の表にも無い。`logs/feedback.md` は同日、「モデル × エフォート」で書くと記録している。週次の表には反映されていない。

### 1.2 月末時点の推奨表（2026-10-31）

フラッグシップと妥当なコスパは、2026-10-31 の週次のまま。Claude 限定だけ、`logs/feedback.md` の「コストは度外視して性能順」に合わせ、週次に載った数値で組み直した。推奨エフォートは週次に無いので、列は空けていない。

| 作業 | フラッグシップ | 妥当なコスパ | Claude 限定（コストを無視した性能順） |
| --- | --- | --- | --- |
| 文章作成・判断 | Claude Opus 5.5 / Gemini 4 Argon / GPT-6 Astra | Claude Sonnet 5.5 / GPT-6.1 Sol / GPT-6.1 Terra | Opus 5.5 / Sonnet 5.5 / Fable 5.1 |
| コーディング | Claude Opus 5.5 / Grok 4.7 / GPT-6 Astra | Grok 4.7 / GPT-6.1 Sol / Claude Sonnet 5.5 | Sonnet 5.5 / Opus 5.5 / 3位は確認できなかった |
| 複雑なコーディング | Claude Opus 5.5 / Gemini 4 Argon / Muse Wonder | Gemini 4 Argon（導入価格〜11/30） / Grok 4.7 / GPT-6.1 Sol | 確認できなかった |
| レビュー | Claude Opus 5.5 / GPT-6 Astra / Gemini 4 Argon | Claude Sonnet 5.5 / GPT-6.1 Sol / Grok 4.7 | Opus 5.5 / Sonnet 5.5 / Fable 5.1 ※ |
| オーケストレーション | Claude Opus 5.5 / GPT-6 Astra / Gemini 4 Argon | GPT-6.1 Terra / GPT-6.1 Sol / Claude Sonnet 5.5 | Opus 5.5 / Sonnet 5.5 / 3位は確認できなかった |

推奨エフォート: 5作業 × 3枠のすべてで確認できなかった。測定条件として週次に残っている努力設定は、この節の末尾に分けて書いた。

#### Claude 限定を性能順にした根拠

- 文章作成・判断。GDPval-AA は Opus 5.5 が 1846、Sonnet 5.5 が 1844、Fable 5.1 が 1735。[A1][A4]
  週次の並びは Opus / Fable / Sonnet。Fable を Sonnet の前に置いた説明には、旧フラッグシップであることと $10/$50 が含まれる。コストを外すと Sonnet が Fable の前になる。Haiku の GDPval は週次に無い。
- コーディング。Terminal-Bench 4.0 は Sonnet 5.5 が 70.6%、Opus 5.5 が 66.4%、Fable 5.1 が 55.8%。[A1][A4]
  Haiku 5.5 の Terminal-Bench は週次に無い。FrontierCode は Opus の 54.4% と Haiku の 46.4% だけで、Fable の値は無い。[A1][A3]
  1位と2位は Terminal-Bench で決まる。3位は Fable と Haiku のどちらとも確認できなかった。週次は Sonnet / Opus / Haiku で、Haiku を3位にした理由は $0.10/$0.50（プロンプト 100k 以下）と、小さく切った作業向けであること。
- 複雑なコーディング。FrontierCode v1.1 が週次にある Claude は、Opus 5.5 の 54.4% だけ。[A1]
  Terminal-Bench では Sonnet 70.6%、Opus 66.4%、Fable 55.8%。公式のモデル一覧は、Opus の eval が足りない長時間作業に Fable を案内している。週次が Fable を2位にした文には「価格は $10/$50 なので保険としての2位」とある。[A1][A6]
  長時間作業の案内と Terminal-Bench で前後が揃わない。単一の性能順は確認できなかった。週次の並びは Opus / Fable / Sonnet。
- レビュー（※）。レビュー専用の Claude 間の数値は週次に無い。GDPval-AA では Opus、Sonnet、Fable の順で、週次の並びと一致する。Terminal-Bench では Sonnet が Opus の前になる。表の ※ は GDPval-AA 順であり、レビュー専用の単一指標では確認できなかった。
- オーケストレーション。Opus 5.5 の OSWorld 2.1 は 81.8%（部分点込み）、AutomationBench は 40.0%。Sonnet 5.5 の OSWorld 2.1 は 80.1%（部分点）。[A1][A4]
  Sonnet の AutomationBench、Haiku と Fable のオーケストレーションの数値は週次に無い。3位は確認できなかった。週次は Opus / Sonnet / Haiku（サブエージェント）で、Haiku の根拠は Anthropic 自身のサブエージェント推奨であり、性能値ではない。[A3]

#### 週次に残っている努力条件（推奨値ではない）

枠に対する「このエフォートを使え」は、どの号にも無い。順位の根拠として書かれていた測定条件だけを残す。

- Terra を文章のコスパ3位にした根拠の一つは、最大努力の内部誤り率 4.3% が Astra / Sol に近いこと。[O7]
- Terra をコーディングに入れなかった根拠は、Terminal-Bench 4.0 の最大努力 50.3%。[O7]
- Terra をオーケストレーションのコスパ1位にした根拠は、Agents’ Last Exam の中程度の努力で Astra と同等なこと、および最大努力では Opus 5.5 よりトークン効率が3倍超なこと。[O7]
- Sol をオーケストレーションのコスパに残した根拠には、AutomationBench の medium effort で Opus を 2.2 ポイント上回る、という公式の主張がある。[O4]

pstack の slug に付いている `xhigh` や `high` は、第2節の提案であり、上の推奨表のエフォートではない。

## 2. pstack の見直し提案（月末時点）

設定は変えていない。ここは 2026-10-31 の週次にある提案のまとめ。既定値は、同日に [setup-pstack の SKILL.md](https://github.com/cursor/plugins/blob/main/pstack/skills/setup-pstack/SKILL.md) の raw を開いて確認したもので、10-16 から役割とモデルの対応は変わっていない。

```
# budget: large (xhigh)
feature, refactoring: grok-4.7-xhigh-fast
bug-fix: grok-4.7-xhigh-fast
perf-issue: grok-4.7-xhigh-fast
hillclimb: grok-4.7-xhigh-fast
judgment and prose: claude-opus-5-5-xhigh
hardest tasks: claude-opus-5-5-xhigh
how explorer: grok-4.7-xhigh-fast
how explainer: claude-opus-5-5-xhigh
why investigators: grok-4.7-xhigh-fast
why synthesizer: claude-opus-5-5-xhigh
reflect tooling: grok-4.7-xhigh-fast
reflect judgment, divergent, synthesizer: claude-opus-5-5-xhigh
arena runners: claude-opus-5-5-xhigh, grok-4.7-xhigh-fast
arena cross-judge pool: claude-opus-5-5-xhigh, grok-4.7-xhigh-fast
swarm workers: grok-4.7-xhigh-fast
architect runners: claude-opus-5-5-xhigh, grok-4.7-xhigh-fast
interrogate reviewers: claude-opus-5-5-xhigh, grok-4.7-xhigh-fast
```

判断・文章と最難タスクを Opus 5.5（`claude-opus-5-5-xhigh`）、実装系を Grok 4.7（`grok-4.7-xhigh-fast`）に置く既定は、第1節とおおむね合う、と 10-31 は書いている。

月末時点の提案は次の7件。1〜4は 10-17 までに出そろい、5は 10-24、6と7は 10-31 に追加された。10-31 で slug の有無を実行環境の一覧と照合している。

1. arena / architect / interrogate のパネルに Gemini 4 Argon（`gemini-4-argon-high`）を3本目として加える。この実行環境の一覧には `low` / `medium` / `high` があり、`xhigh` は無い。導入価格は 11/30 まで。
2. swarm workers のうち狭い作業（要約・調べもの）に Claude Haiku 5.5 を試す。プロンプト 100k 以下は $0.10/$0.50。この実行環境の一覧に Haiku の slug は無い。
3. interrogate reviewers に GPT 系を足す案は残す。一覧にあるのは `gpt-5.6-sol-*` で、`gpt-6.1-sol` は無い。6.1 Sol の slug が確認できるまで割り当てない。
4. コーディング系（feature / bug-fix / hillclimb）で `claude-sonnet-5-5-xhigh` を試す。Terminal-Bench 4.0 は Sonnet 70.6%、Opus 66.4%。この slug は一覧にある。
5. arena / architect のパネルに Muse Wonder（`muse-wonder-1.0-xhigh`）を加える。この slug は一覧にある。超長期 SWE の公式比較が強く、API 単価は Opus と同じ $4/$20。
6. オーケストレーション寄りの swarm には GPT-6.1 Terra が API 上は有力（$1/$5、コンピュータ操作のタスク単価が低い）。一覧に `gpt-6.1-terra` は無い。slug が確認できるまで割り当てない。
7. Gemini 4 Carbon が開発者向けに出たら、hardest tasks の候補として見直す。現時点では API も slug も無い。

## 3. 10月に話題性が高かったニュース

週次に載った項目から5件に絞った。基準は次のどちらか。

- 週次が Yahoo!ニュースまたは Reuters への配信を書いている
- 月内の推奨表の順位を動かしたモデル発表、または10月中に一般提供され月末の推奨表の複数枠に残っているモデル発表

各リンクは 2026-10-31 に開き直した。

同じ基準では外した週次の項目: Gemini 4 Carbon、Genie 4、Muse Spark Open、Claude Duet、DeepSeek-V4.1-Flash-1017、Decisions API、TanStack Start 1.0、TanStack Redact、Bun の `bun fmt` など。Carbon を推奨表の対象外にした理由は第1節。

### Muse Wonder（Meta、10/12）

Meta が 10/12 に発表した Muse Wonder は、API $4/$20・コンテキスト 1M で、DeepSWE 1.1 が 78.8、SWE-Marathon が 53.1 だったため、10/24 の週次から複雑なコーディングのフラッグシップ3位になった。Full は Muse Code の有料プラン限定で、トークン課金の推奨表には入っていない。

- https://dev.meta.ai/resources/blog/build-with-muse-wonder
- https://dev.meta.ai/models/muse-wonder

### Gemini 4 Argon の一般提供（Google、10/13）

Google は 10/13 に Gemini 4 Argon を一般提供した。Vals Index 1位で、API、AI Studio、Gemini アプリ（Pro/Ultra 限定）、Antigravity で使え、11/30 までの導入価格は $2/$10（12/1 から $4/$20）である。

- https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-argon/
- https://cloud.google.com/blog/products/ai-machine-learning/gemini-4-argon-available-on-google-cloud
- https://aistudio.google.com/learn/gemini-4-argon-developer-guide
- https://ai.google.dev/gemini-api/docs/pricing

### OpenAI モデルの Google Cloud 提供（10/21）

OpenAI は 10/21 に、GPT-6 Astra、GPT-6.1 Sol、GPT-6 Luna と Codex を Google Cloud Model Garden の限定プレビューで提供すると発表し、週次は Yahoo!ニュースでも配信されたと書いている（その記事 URL は今回 404 のため、出典は公式ページだけ）。GA は数週間以内で、Microsoft は主クラウドのまま、と週次が公式発表からまとめている。

- https://openai.com/index/openai-models-google-cloud
- https://cloud.google.com/blog/products/ai-machine-learning/google-cloud-brings-openai-models-to-customers

### GPT-6.1 Terra（OpenAI、10/26）

OpenAI は 10/26 に、視覚理解とコンピュータ操作、文章向けの GPT-6.1 Terra を出した。API は `gpt-6.1-terra`、標準価格は $1 / キャッシュ入力 $0.05 / $5、コンテキストは 1,050,000 で、Terminal-Bench 4.0 は最大努力で 50.3%、難しいコーディングは Sol と Astra を公式が推奨している。

- https://openai.com/index/introducing-gpt-6-1-terra/
- https://developers.openai.com/api/docs/models/gpt-6.1-terra

### Mistral Large 4 のオープンウェイト（Mistral、10/29）

Mistral は 10/29 に Mistral Large 4（Le Chonk）の重みを公開した。総パラメータ約 1 兆、コンテキスト 1M、API は $0.70 / キャッシュ $0.07 / $2.10、公式の Terminal-Bench 4.0 は 41%、ライセンスは改変 MIT で、週次は Reuters 配信と Yahoo!ニュース掲載を書いている。

- https://mistral.ai/news/mistral-large-4-oss/
- https://huggingface.co/blog/mistral-large4
- https://www.yahoo.com/news/articles/mistral-ai-publicly-releases-large-140336526.html

## 4. 実行ログから見た改善点と手順の変更提案

提案だけを書く。スキル、週次のテンプレート、pstack の設定は変えていない。実施は依頼者の了承後。

10月の実行ログからは、個別の採否理由を読めなかった。`logs/runs/README.md` は、実行日の `logs/runs/YYYY-MM-DD.md` にモデルとエフォート、表の変更、ニュースの採否、出典の食い違い、前回の反映、次回メモを残す、と定めている。`logs/feedback.md` の 2026-10-31 も同じ手順を「反映」と書いている。日付付きファイルは 10月分が無い。

週次と feedback を突き合わせて見えた点と、手順への提案:

1. 実行ログを完了条件にする。週次または月次を出した回は、同じ PR に `logs/runs/YYYY-MM-DD.md` を含める。ファイルが無い月は、月次に「確認できなかった」と書く（今回そうしている）。
2. 推奨表のセルを「モデル × エフォート」にする。10-31 の feedback は反映済みと書いているが、同日の週次表にエフォートは無い。根拠ベンチの努力条件（最大努力、medium effort など）を同じ行に書き、指定できない枠は「確認できなかった」と書く。pstack の `xhigh` を、週次の推奨エフォートとして流用しない。
3. Claude 列を並べるとき、価格と「保険」を理由に使わない。文章作成の週次は Fable 5.1（GDPval-AA 1735、$10/$50）を Sonnet 5.5（1844）の前に置いている。セルの横に、その作業の主ベンチの数値を併記する。数値が指標ごとに前後する作業は、1位を一つに確定せず「確認できなかった」と書く。
4. 前号と数値が違うときは、どのページのどの表かを1行書く。説明が無い例は、Astra の Terminal-Bench 4.0（57.9% → 57.7% → 57.9%、出典はいずれも [A1]）。説明がある例は、Sol のキャッシュ入力（$0.20 は GPT-6 Sol との混同、と 10-24）と、Sonnet の GDPval-AA（Haiku 掲載ページの 1840 と Sonnet 自身の表の 1844、と 10-31）。
5. 「前回からの変化」は、前号の表とセルが違うものだけを書く。10-17 は「Argon をコスパ枠の2位に推奨」と書くが、表は 10-16 と同じで、複雑なコーディングのコスパ1位が Argon である。
6. 月次で週次の出典 URL を開き直す。死んだリンクは月次の出典にしない。週次ファイルは書き換えない。今回、2026-10-24 の Yahoo!ニュース URL（`https://news.yahoo.co.jp/articles/dbfd78140ec7909f8377fac7bb0f17706299f81e`）は 404 だった。同じ項目の公式ページは開けた。
7. 月次の対象範囲を、リポジトリにある週次の日付で書く。欠けている週は「確認できなかった」とする。今回、10/1〜10/8 がそれに当たる。

## 出典

記号は 2026-10-31 の週次に合わせた。号によって同じ記号が別の URL を指す。10-17 の [G2] は下の Cloud 告知、[G3] は AI Studio のガイド。10-24 の [G3] は OpenAI モデルの Google Cloud 告知で、このファイルの [G3] はそちら。このファイルの [G2] は料金ページ。開き直して本文に使ったものだけを載せる。

- [A1] https://www.anthropic.com/claude-opus-5-5
- [A3] https://www.anthropic.com/claude-haiku-5-5
- [A4] https://www.anthropic.com/claude-sonnet-5-5
- [A6] https://platform.claude.com/docs/en/docs/about-claude/models
- [G1] https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-argon/
- [G2] https://ai.google.dev/gemini-api/docs/pricing
- Argon の Cloud 告知（10-17 の G2）: https://cloud.google.com/blog/products/ai-machine-learning/gemini-4-argon-available-on-google-cloud
- Argon の AI Studio ガイド（10-17 の G3）: https://aistudio.google.com/learn/gemini-4-argon-developer-guide
- [G3] https://cloud.google.com/blog/products/ai-machine-learning/google-cloud-brings-openai-models-to-customers
- [G4] https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-carbon/
- [O1] https://developers.openai.com/api/docs/pricing
- [O4] https://openai.com/index/introducing-gpt-6-1-sol/
- [O6] https://openai.com/index/openai-models-google-cloud
- [O7] https://openai.com/index/introducing-gpt-6-1-terra/
- [O8] https://developers.openai.com/api/docs/models/gpt-6.1-terra
- [X1] https://docs.x.ai/developers/grok-4-7
- [M1] https://dev.meta.ai/resources/blog/build-with-muse-wonder
- [M2] https://dev.meta.ai/models/muse-wonder
- [M4] https://mistral.ai/news/mistral-large-4-oss/
- [M5] https://huggingface.co/blog/mistral-large4
- [Y1] https://www.yahoo.com/news/articles/mistral-ai-publicly-releases-large-140336526.html
- pstack の既定値: https://github.com/cursor/plugins/blob/main/pstack/skills/setup-pstack/SKILL.md
