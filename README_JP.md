
# LooperPro (Android, Kotlin)

シンプルな**最大10トラック対応**のルーパーアプリです。

- マイク録音（各トラック最大60秒）
- ループ再生
- BPM設定＆クオンタイズ（録音開始は拍頭に合わせる簡易版）
- 5つのエフェクト（Reverb / Delay / Pitch Up / Pitch Down / Lo-Fi）
- WAV保存（Music/LooperPro）
- ブラック・ミニマルUI

> 注意：ピッチシフトは**軽量な独自実装**のため、音質は簡易です。±2半音程度を想定。
> それ以上の半音移動や高品質を求める場合は TarsosDSP などのライブラリ導入をご検討ください。

## 動作環境

- Android Studio Giraffe 以降
- Kotlin 1.9+
- minSdk 26 / targetSdk 34

## ビルド手順

1. Android Studioで本プロジェクトを開く
2. 依存が落ちてきたらそのまま `Run`（デバイスは実機推奨）
3. マイク許可を許可する

## 使い方

1. 画面上部で **BPM** を設定し、**Quantize** をONにしておくと録音開始が拍頭に揃います。
2. 各トラック行の **Rec** を押して録音開始、もう一度押すと停止・確定。
3. **FX** でエフェクトを選択（複数可）。録音確定後に適用されます（オフライン適用）。
4. **Play** で全トラック同時にループ再生。**Mute** で各トラックの音量をミュート。
5. 💾 で各トラックを **WAVで保存**。Android 10 以上は「Music/LooperPro」に保存されます。

## 制限・補足

- ピッチUp/Downは簡易アルゴリズムです（±2半音程度推奨）。
- ディレイは固定で約300ms、フィードバック35%（軽量化のため）。
- クオンタイズは録音開始の簡易補正です。より厳密な小節合わせは今後の改良点です。
- エフェクトは録音確定時に**オフライン適用**（処理後の波形を保存）でCPU負荷を抑えています。
- 子供向けスキンは `res/values/colors.xml` やレイアウトの差し替えで対応予定。

## ファイル構成

- `app/src/main/java/com/example/looperpro/audio/AudioEngine.kt` … ミキシング・再生
- `app/src/main/java/com/example/looperpro/audio/Track.kt` … 録音・FX適用・ループ
- `app/src/main/java/com/example/looperpro/audio/Effects.kt` … 簡易エフェクト集
- `app/src/main/java/com/example/looperpro/audio/WavIO.kt` … WAV書き出し
- `app/src/main/java/com/example/looperpro/MainActivity.kt` … UI制御
- `app/src/main/res/layout/row_track.xml` … トラック行
- `app/src/main/res/layout/dialog_effects.xml` … FXダイアログ

## 既知の改善ポイント

- ピッチ処理の高音質化（ライブラリ導入で改善可能）
- メトロノームのクリック精度向上
- トラック個別の音量スライダー / パン
- 複数トラックのエフェクト同時リアルタイム適用（現在はオフライン）

---

© 2025-08-13 LooperPro Sample
