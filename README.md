# 名古屋紹介 impress.js プレゼンテーション

impress.jsを使用した名古屋市紹介のシングルページHTMLプレゼンテーションです。

## impress.jsとは

impress.jsは、CSSの3D変形機能を活用した革新的なプレゼンテーションフレームワークです。従来のスライド形式とは異なり、3D空間上でスライドを自由に配置し、ダイナミックなトランジションを実現します。

## 動作原理

### 1. 基本構造

```html
<div id="impress" data-transition-duration="1000">
  <div id="title" class="step" data-x="0" data-y="0" data-scale="1.5">
    <!-- スライドコンテンツ -->
  </div>
</div>
```

- `#impress`: すべてのスライドを含むコンテナ
- `.step`: 個々のスライドを表すクラス
- データ属性でスライドの3D位置と変形を指定

### 2. 位置指定データ属性

各スライド（`.step`要素）は以下のデータ属性で位置と状態を制御：

- `data-x`: X軸の位置（ピクセル）
- `data-y`: Y軸の位置（ピクセル）  
- `data-z`: Z軸の位置（奥行き）
- `data-rotate`: Z軸回転（度）
- `data-rotate-x`: X軸回転（度）
- `data-rotate-y`: Y軸回転（度）
- `data-rotate-z`: Z軸回転（度）
- `data-scale`: スケール（拡大縮小）

### 3. アニメーション機構

#### CSSトランジション
```css
.step {
  opacity: 0;
}

.step.active {
  opacity: 1;
  transition: opacity 1s;
}
```

- 非アクティブスライドは透明（`opacity: 0`）
- アクティブスライドは不透明（`opacity: 1`）に遷移
- CSS transitionで滑らかなアニメーションを実現

#### 段階的アニメーション
```css
.step.active ul li:nth-child(1) { transition-delay: 0.1s; }
.step.active ul li:nth-child(2) { transition-delay: 0.2s; }
.step.active ul li:nth-child(3) { transition-delay: 0.3s; }
```

リストアイテムに段階的な遅延を設定し、順番に表示される効果を実現。

### 4. カメラワーク

impress.jsは仮想カメラを以下のように制御：

1. 現在のスライドの3D位置を計算
2. カメラを該当位置に移動
3. 適切な回転とスケールを適用
4. CSS 3D transformで全体をレンダリング

### 5. このプレゼンテーションの構成

```
タイトル (x:0, y:0, scale:1.5)
    ↓
概要 (x:1000, y:0, rotate:10°)
    ↓
歴史 (x:2000, y:400, rotate:-10°)  
    ↓
観光名所 (x:1000, y:1000, rotate:20°)
    ↓
名古屋めし (x:0, y:800, rotateZ:-15°, rotateY:30°)
    ↓
文化・祭り (x:-1000, y:1000, rotate:-30°)
    ↓
まとめ (x:0, y:0, z:-2000, rotateX:-90°, scale:2)
    ↓
俯瞰ビュー (x:300, y:500, z:-3000, scale:5)
```

### 6. 特殊効果

#### トランジション時間
```html
<div id="impress" data-transition-duration="1000">
```
スライド間の遷移時間を1000ミリ秒に設定。

#### 画像アニメーション
```css
.step img {
  opacity: 0;
  transform: scale(0.8);
  transition: all 0.6s ease-out 0.3s;
}

.step.active img {
  opacity: 1;
  transform: scale(1);
}
```
画像は0.3秒の遅延後、拡大しながらフェードイン。

#### グラデーション背景
```css
body {
  background: radial-gradient(rgb(240,240,240) 0%, rgb(200,200,200) 100%);
}
```
円形グラデーションで奥行き感を演出。

## 操作方法

- **→** または **Space**: 次のスライド
- **←**: 前のスライド
- **Tab**: スライド一覧
- **Esc**: 俯瞰ビュー

## 技術的特徴

1. **CSS3 3D Transform**: ハードウェアアクセラレーションによる滑らかなアニメーション
2. **JavaScript制御**: impress.jsライブラリがナビゲーションとアニメーションを管理
3. **レスポンシブ**: viewportメタタグで様々なデバイスに対応
4. **CDN利用**: 外部ライブラリ（impress.js、Google Fonts）はCDNから読み込み

## ブラウザサポート

モダンブラウザ（Chrome、Firefox、Safari、Edge）で動作。CSS 3D transformをサポートしている必要があります。

## カスタマイズ

各スライドの位置、回転、スケールを調整することで、独自のプレゼンテーションフローを作成できます。CSSアニメーションをカスタマイズすることで、さらに高度な視覚効果も実現可能です。