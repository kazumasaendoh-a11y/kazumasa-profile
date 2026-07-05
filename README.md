# KAZUMASA ENDOH Brand Homepage

名刺裏面のQRコードから飛ばすための、静的な1ページブランドホームページです。

## Files

- `index.html`
- `styles.css`
- `business-card-front.svg`
- `business-card-back.svg`

## Local Preview

ブラウザで `index.html` を直接開くと確認できます。

ローカルサーバーで確認する場合:

```sh
python3 -m http.server 4173
```

その後、ブラウザで `http://127.0.0.1:4173/` を開きます。

## Link Placeholders

リンク先は `index.html` 上部の `SITE_LINKS` で差し替えます。

```html
<script>
  const SITE_LINKS = {
    instagram: "https://instagram.com/iroai_endoh",
    contact: "mailto:kazumasa.endoh@gmail.com",
    salonInstagram: "https://www.instagram.com/plane___official",
    salonCall: "tel:0782208835",
    salonMap: "https://www.google.com/maps/search/?api=1&query=plane%20..."
  };
</script>
```

リンク表示そのものは `<nav class="link-list">` 内にあります。表示名を変える場合は、該当する `<a>` のテキストを変更してください。

現在の仮URL:

- Instagram: `https://instagram.com/iroai_endoh`
- Contact: `mailto:kazumasa.endoh@gmail.com`
- Salon Instagram: `https://www.instagram.com/plane___official`
- Salon Call: `tel:0782208835`
- Salon Map: Google Maps search URL for `plane 兵庫県神戸市北区上津台5-6-4`

OGP用URLも公開後に差し替えてください。SNSや検索エンジン向けの情報なので、JavaScriptではなくHTML内のmetaタグを直接更新します。

```html
<meta property="og:url" content="https://example.com/">
```

## Vercel Minimal Setup

このサイトは静的HTML/CSS/JavaScriptのみで動きます。Vercel公開に必要な最小構成は以下です。

- `index.html`
- `styles.css`

ビルドコマンド、フレームワーク設定、追加パッケージは不要です。

## Deploy To Vercel

1. GitHubで新しいリポジトリを作成します。
2. このフォルダの内容をリポジトリへアップロードします。
3. Vercelにログインします。
4. Vercelで「Add New Project」を選びます。
5. 作成したGitHubリポジトリを選択します。
6. Framework Presetは `Other` のままでOKです。
7. Build Commandは空欄にします。
8. Output Directoryも空欄のままにします。
9. Deployを押します。
10. 発行されたVercel URLを `og:url` に設定します。
11. 同じURLを名刺裏面QRコードのリンク先に使います。

独自ドメインを使う場合は、VercelのProject SettingsからDomainsを追加してください。

## Pre-Publish Checklist

- `SITE_LINKS` のInstagram/Contact URLを本番URLへ差し替えた
- `<meta property="og:url">` をVercel URLまたは独自ドメインへ差し替えた
- `<title>` と `description` が公開内容に合っている
- スマホ幅でHero、Building、Linksの余白を確認した
- Linksの各リンクをクリックして正しいページに飛ぶことを確認した
- QRコード生成時のURLが公開URLと一致している
- Vercelの公開URLをシークレットウィンドウで確認した

## Business Card SVG Notes

名刺SVGは日本標準サイズ `91mm x 55mm` に、四辺 `3mm` の塗り足しを加えた `97mm x 61mm` で作成しています。

- Trim starts at: `x = 3mm`, `y = 3mm`
- Trim size: `91mm x 55mm`
- Safe area guideline: trim端から内側に最低 `3mm`

裏面右下はQRコード配置用に余白を残しています。推奨QRサイズは `18mm x 18mm` から `22mm x 22mm` です。
