# デザイン向け AI モデル比較（アドホック調査、2026-11-01 JST）

週次ルーティンとは別に、Takashi の依頼で単発に実施した調査。対象は「デザイン」（UI・LP・図解などの見た目の制作。今回はコード生成型の UI に限る）。

根拠は人の投票で順位が決まる2つの公開リーダーボード。1位が分かれるため両方を併記する。
- WebDev Arena（フロントエンドを作るエージェント作業、最終更新 10/27）: https://arena.ai/leaderboard/code/webdev
- Design Arena（単一 HTML の Website / UI Component などの見た目、最終更新 11/1 09:06〜09:08 JST）: https://www.designarena.ai/leaderboard

## 1) フラッグシップ（コスト無視）
| # | モデル | 推奨エフォート | 理由 | 出典 |
|---|---|---|---|---|
| 1 | Claude Opus 5.5 | Max | WebDev Arena で 1810 の単独1位（2位と +37）。Design Arena 総合も 1385 で3位、1位との差は誤差の範囲。エフォート別の公開データなし（WebDev の掲載が Max のみ） | [WebDev](https://arena.ai/leaderboard/code/webdev) / [DA総合](https://www.designarena.ai/leaderboard) |
| 2 | GPT-6 Astra | xhigh | Design Arena 総合1位（1389）、UI Component 1位（1397）。UI Component では xhigh 1397 が max 1370 を上回る。WebDev は Max で 1773 の2位 | [DA UI](https://www.designarena.ai/leaderboard/ui-components) / [WebDev](https://arena.ai/leaderboard/code/webdev) |
| 3 | Muse Wonder | max | Design Arena の Website で1位（1370）、総合2位（1386）。ただし WebDev は 1652 の20位で、エージェント型の Web 開発では弱め。API 版で比較（上位の Full は Muse Code の有料プラン限定） | [DA Website](https://www.designarena.ai/leaderboard/website) / [Meta](https://dev.meta.ai/resources/blog/build-with-muse-wonder) |

## 2) 妥当なコスパ（入力 / 出力、$ per 1M tokens）
| # | モデル | 推奨エフォート | 理由 | 価格 | 出典 |
|---|---|---|---|---|---|
| 1 | Claude Sonnet 5.5 | xhigh | WebDev で xHigh が 1770。High の 1711 より +59 高く、Astra（$10/$50）とほぼ同点。Anthropic も「デザインに鋭い目」があると説明 | $2/$10 | [WebDev](https://arena.ai/leaderboard/code/webdev) / [Anthropic](https://www.anthropic.com/claude-sonnet-5-5) |
| 2 | Muse Spark 1.3 | xhigh（WebDev 型の作業なら Max） | Design Arena の Website で2位（1355）、Max の 1345 より上。WebDev では Max 1656 が xHigh 1620 を上回る | $1.25/$4.25 | [DA Website](https://www.designarena.ai/leaderboard/website) / [Meta価格](https://dev.meta.ai/docs/pricing-rate-limits) |
| 3 | GPT-6.1 Sol | Max | WebDev で Max が 1751 の5位、Design Arena 総合4位（1360）。Design Arena 側の Sol にはエフォート表記なし | $2/$10（272K 超は $4/$15） | [WebDev](https://arena.ai/leaderboard/code/webdev) / [OpenAI価格](https://developers.openai.com/api/docs/pricing) |

表外の候補: DeepSeek V4.1 Flash（$0.15/$0.60、WebDev 1665）。

## 3) Claude 限定（性能順、コスト無視）
| # | モデル | 推奨エフォート | 理由 | 出典 |
|---|---|---|---|---|
| 1 | Opus 5.5 | Max | WebDev で全体1位。公式もゲーム生成で「グラフィックと仕上げ」が最高だったと記載。デザイン作業のエフォート別データなし | [WebDev](https://arena.ai/leaderboard/code/webdev) / [Anthropic](https://www.anthropic.com/claude-opus-5-5) |
| 2 | Sonnet 5.5 | xhigh | WebDev で xHigh 1770 は High 1711 より明確に上。Design Arena の UI Component でも 1375 で Opus の 1378 とほぼ同じ | [WebDev](https://arena.ai/leaderboard/code/webdev) / [DA UI](https://www.designarena.ai/leaderboard/ui-components) |
| 3 | Fable 5.1 | Max | WebDev 1746、Design Arena 総合 1333。上の2つより低く、$10/$50 と高価。エフォート別データなし | [WebDev](https://arena.ai/leaderboard/code/webdev) / [DA総合](https://www.designarena.ai/leaderboard) |

Haiku 5.5 は WebDev が High で 1589 と大きく離れるため除外。

## pstack への割り当て案（提案のみ、設定は未変更）
デザイン役の普段の実装は `claude-sonnet-5-5-xhigh`、仕上げや arena の審査は `claude-opus-5-5-xhigh`。Sonnet は Astra と同等の WebDev スコアを半額以下で出せる。10/31 号の既定設定にはデザイン専用の役割がないため、feature や arena runners に足す形になる。

## 確認できなかったこと
- Opus 5.5、Muse Wonder、Fable 5.1 のデザイン作業でのエフォート別スコア（リーダーボードには単一設定のみ）。
- Design Arena の Opus 5.5 / Sonnet 5.5 / GPT-6.1 Sol の測定エフォート（表記なし）。
- Gemini 4 Carbon は WebDev が High で 1768 の4位だが Preliminary（暫定）かつ一般 API 未提供のため表外。
- バナー・図解・画像生成の品質を比べるリーダーボード（今回はコード生成型 UI のみ）。
- Muse 系、DeepSeek、Kimi が Cursor / pstack で使えるか（slug）。
