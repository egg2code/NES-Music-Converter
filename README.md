# Browser NES NSF Sketcher

WAV/MP3 をブラウザだけで解析し、簡易的に NES チャンネルへ割り当てた `NSF` を生成するシングルページアプリです。

## できること

- WAV / MP3 のアップロード
- 波形表示と再生
- 主旋律を最大 3 音まで推定して `Pulse1 + Pulse2 + Triangle` へ割り当て
- ドラム成分を `Noise` チャンネルへ近似
- `NSF` ファイルをダウンロード

## 重要な注意

- これは **完全自動の下書き生成** です。精度は素材に強く依存します。
- NES 実機制約に合わせるため、和音は 2Pulse + 1Triangle の範囲で近似します。
- 高品質なチップチューン化には、FamiTracker/FamiStudio 等での後編集を推奨します。

## ローカルで試す

`index.html` をブラウザで開くだけで動きます。

## GitHub Pages へ公開

1. このリポジトリを GitHub に push
2. リポジトリの `Settings` -> `Pages`
3. `Build and deployment` で `Deploy from a branch`
4. ブランチを `main` (または既定ブランチ)、フォルダを `/root` に設定
5. 保存して公開 URL を開く

## 技術メモ

- 解析: フレーム単位 + Goertzel で候補音程を抽出
- 出力: ブラウザ内で NSF ヘッダと 6502 再生ルーチンを組み立ててバイナリ化
- 外部サーバー不要 (GitHub Pages で動作)
