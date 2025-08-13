
# LooperPro — APKを同梱したZIPを作るための最短手順（Android Studio不要）

このプロジェクトには、GitHub Actions のワークフローが同梱されています。
PCのブラウザだけで **APK（app-debug.apk）** を自動生成し、生成後にZIPへ同梱できます。

## 手順（2〜5分、完全無料）

1. GitHubにログインし、新規リポジトリを作成（公開/非公開どちらでもOK）。
2. リポジトリ画面で **Add file → Upload files** をクリックし、
   このフォルダ一式をアップロード（ZIPのままアップして「Extract」でも可）。
3. 上部タブ **Actions** を開き、ワークフロー「Android APK (Debug) Build」を **Run workflow**。
4. 数分後、ワークフローのページ最下部の **Artifacts** に `app-debug-apk` が表示されます。
   クリックして **`app-debug.apk`** をダウンロード。

## APKを同梱したZIPの作り方（任意）

- ダウンロードした `app-debug.apk` をこのプロジェクトの任意の場所（例：`/Builds/`）に置く。
- そのままフォルダ全体をZIP圧縮すれば、「ソース + APK 同梱ZIP」が完成です。

> 初回インストール時は、スマホ側で「不明なアプリのインストールを許可」をONにしてください。

（ワークフローは `.github/workflows/android_debug_build.yml` にあります。）

更新日: 2025-08-13
