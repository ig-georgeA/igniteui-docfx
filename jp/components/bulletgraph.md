﻿---
title: Bullet Graph コンポーネント - ネイティブ Angular | Ignite UI for Angular
_description: Ignite UI for Angular の Bullet Graph コンポーネントはスケールに比較されるメジャーのリニア ビューを表示します。
_keywords: Ignite UI for Angular, Angular, ネイティブ Angular コンポーネント スイート, ネイティブ Angular コントロール, ネイティブ Angular コンポーネント, ネイティブ Angular コンポーネント ライブラリ, Angular ブレット グラフ コンポーネント, Angular ブレット グラフ
_language: ja
---
## Bullet Graph

Ignite UI for Angular の Bullet Graph コンポーネントは、目盛り上でリニアと簡潔なメジャーの比較を表示します。

### デモ

ブレット グラフ コンポーネントは、きれいなデータ表現を作成するための多数の機能をサポートします。ブレット グラフは、目標に対する進捗状況、評価の範囲、複数の測定比較を表現する際に最も効率的で効果的なグラフの 1 つです。ブレット グラフは、水平または垂直のわずかな領域で、ゴールに至る進捗、評価の範囲、複数の測定比較を表現するための最も効率的で効果的な方法の 1 つです。

以下のサンプルは、同じゲージでいくつかのプロパティを設定して全く異なるゲージにする方法を示します。

<div class="sample-container" style="height: 125px">
    <iframe id="bullet-graph-animation-iframe" src='{environment:demosBaseUrl}/bullet-graph-animation' width="100%" height="100%" seamless frameBorder="0" onload="onSampleIframeContentLoaded(this);"></iframe>
</div>
<div>
    <button data-localize="stackblitz" class="stackblitz-btn"   data-iframe-id="bullet-graph-animation-iframe" data-demos-base-url="{environment:demosBaseUrl}">StackBlitz で開く
    </button>
</div>

<div class="divider--half"></div>

このゲージは、スケール、針、目盛 (1 組)、ラベル (1 組) をサポートします。このコンポーネントには、アニメーション化されたトランジションのサポートも組み込まれています。アニメーションは、`transitionDuration` プロパティの設定で簡単にカスタマイズできます。
ブレット グラフの機能には構成可能な向きや方向、視覚要素やツールチップなどがあります。

### 依存関係
gauges パッケージのインストール時に core パッケージもインストールする必要があります。

`npm install ignite-angular-gauges ignite-angular-core`

ブレット グラフが `NgModule` としてエクスポートされるため、アプリケーションで `AppModule` に _IgxBulletGraphModule_ をインポートする必要があります。

```typescript
// app.module.ts
import { IgxBulletGraphModule } from 'igniteui-angular-gauges/ES5/igx-bullet-graph-module';

@NgModule({
    imports: [
        ...
        IgxBulletGraphModule,
        ...
    ]
})
export class AppModule {}
```

<div class="divider--half"></div>

### 使用方法

以下のコードは、ブレット グラフ コンポーネントを作成し、パフォ―マンス バーと比較目盛マーカー、および 3 つの比較範囲をスケールに構成します。

```html
 <igx-bullet-graph height="100"
                   width="300"
                   minimumValue="5"
                   maximumValue="55"
                   value = "35"
                   targetValue = "43">
    <igx-linear-graph-range startValue="0"
                            endValue="15"
                            Brush="#828181"/>
    <igx-linear-graph-range StartValue="15"
                            EndValue="30"
                            Brush="#AAAAAA"/>
    <igx-linear-graph-range StartValue="30"
                            EndValue="55"
                            Brush="#D0D0D0"/>
 </igx-bullet-graph>
```

<div class="divider--half"></div>

## 構成可能な要素

### 比較メジャー

ブレットグラフは、パフォーマンス値とターゲット値の 2 つのメジャーを表示できます。

パフォーマンス値は、コンポーネントで表示されるプライマリ メジャーでグラフ全体の長さに沿って拡張するバーとして表示されます。ターゲット値は、パフォーマンス値が比較の対象とするメジャーでパフォーマンス バーの向きに対して直角に交わる小さなブロックとして表示されます。

```html
<igx-bullet-graph
    value=50
    valueBrush="DodgerBlue"
    valueStrokeThickness=1
    valueInnerExtent=0.5
    valueOuterExtent=0.65

    targetValue=80
    targetValueBreadth=10
    targetValueBrush="LimeGreen"
    targetValueOutline="LimeGreen"
    targetValueStrokeThickness=1
    targetValueInnerExtent=0.3
    targetValueOuterExtent=0.85

    height="80px" width="400px"
    minimumValue=0 value=50
    maximumValue=100>
</igx-bullet-graph>
```

<div class="sample-container" style="height: 125px">
    <iframe id="bullet-graph-measures-iframe" src='{environment:demosBaseUrl}/bullet-graph-measures' width="100%" height="100%" seamless frameBorder="0" onload="onSampleIframeContentLoaded(this);"></iframe>
</div>
<div>
    <button data-localize="stackblitz" class="stackblitz-btn"   data-iframe-id="bullet-graph-measures-iframe" data-demos-base-url="{environment:demosBaseUrl}">StackBlitz で開く
    </button>
</div>

### 比較範囲
範囲はスケールで指定した値の範囲を強調表示する視覚的な要素です。その目的は、パフォーマンス バー メジャーの質的状態を視覚で伝えると同時に、その状態をレベルとして示すことにあります。

```html
<igx-bullet-graph
    height="80px" width="400px"
    minimumValue=0 value=80 interval=10
    maximumValue=100 targetValue=90

    rangeBrushes ="#C62828, #F96232, #FF9800"
    rangeOutlines="#C62828, #F96232, #FF9800">
    <igx-linear-graph-range
        startValue=0 endValue=40
        innerStartExtent=0.075 innerEndExtent=0.075
        outerStartExtent=0.95 outerEndExtent=0.95>
    </igx-linear-graph-range>
    <igx-linear-graph-range
        startValue=40 endValue=70
        innerStartExtent=0.075 innerEndExtent=0.075
        outerStartExtent=0.95 outerEndExtent=0.95>
    </igx-linear-graph-range>
    <igx-linear-graph-range
        startValue=70 endValue=100
        innerStartExtent=0.075 innerEndExtent=0.075
        outerStartExtent=0.95 outerEndExtent=0.95>
    </igx-linear-graph-range>
</igx-bullet-graph>
```

<div class="sample-container" style="height: 125px">
    <iframe id="bullet-graph-ranges-iframe" src='{environment:demosBaseUrl}/bullet-graph-ranges' width="100%" height="100%" seamless frameBorder="0" onload="onSampleIframeContentLoaded(this);"></iframe>
</div>
<div>
    <button data-localize="stackblitz" class="stackblitz-btn"   data-iframe-id="bullet-graph-ranges-iframe" data-demos-base-url="{environment:demosBaseUrl}">StackBlitz で開く
    </button>
</div>

### 目盛
目盛は、ブレット グラフを読み取りやすくするために、目盛の間隔でスケールを分割して見せる役割を果たします。
- 主目盛 - 主目盛は、スケールの主要な区切りとして使用されます。表示間隔、範囲、およびスタイルは、対応するプロパティを設定し制御できます。
- 補助目盛 - 補助目盛は主目盛を補助し、スケールの数値を読み取りやすくするために追加して使用します。主目盛と同じ方法でカスタマイズできます。

```html
<igx-bullet-graph
    height="80px" width="400px"
    minimumValue=0 value=70 interval=10
    maximumValue=100 targetValue=90

    tickBrush="DodgerBlue"
    ticksPreTerminal=0
    ticksPostInitial=0
    tickStrokeThickness=2
    tickStartExtent=0.2
    tickEndExtent=0.075

    minorTickCount=4
    minorTickBrush="DarkViolet"
    minorTickEndExtent=0.1
    minorTickStartExtent=0.2
    minorTickStrokeThickness=1>
</igx-bullet-graph>
```

<div class="sample-container" style="height: 125px">
    <iframe id="bullet-graph-tickmarks-iframe" src='{environment:demosBaseUrl}/bullet-graph-tickmarks' width="100%" height="100%" seamless frameBorder="0" onload="onSampleIframeContentLoaded(this);"></iframe>
</div>
<div>
    <button data-localize="stackblitz" class="stackblitz-btn"   data-iframe-id="bullet-graph-tickmarks-iframe" data-demos-base-url="{environment:demosBaseUrl}">StackBlitz で開く
    </button>
</div>

### ラベル
ラベルはスケールのメジャーを示します。

```html
<igx-bullet-graph
   height="80px" width="400px"
    minimumValue=0 value=70 interval=10
    maximumValue=100 targetValue=90
    labelInterval=10
    labelExtent=0.025
    labelsPreTerminal=0
    labelsPostInitial=0
    fontBrush="DodgerBlue"
    font="11px Verdana">
</igx-bullet-graph>
```

<div class="sample-container" style="height: 125px">
    <iframe id="bullet-graph-labels-iframe" src='{environment:demosBaseUrl}/bullet-graph-labels' width="100%" height="100%" seamless frameBorder="0" onload="onSampleIframeContentLoaded(this);"></iframe>
</div>
<div>
    <button data-localize="stackblitz" class="stackblitz-btn"   data-iframe-id="bullet-graph-labels-iframe" data-demos-base-url="{environment:demosBaseUrl}">StackBlitz で開く
    </button>
</div>

### バッキング
バッキング要素はブレット グラフ コントロールの背景と境界線を表します。常に最初に描画される要素でラベルやメモリなどの残りの要素は互いにオーバーレイします。

```html
<igx-bullet-graph
    height="80px" width="400px"
    minimumValue=0 value=70
    maximumValue=100 targetValue=90
    interval=10
    tickBrush="DodgerBlue"
    ticksPreTerminal=0
    ticksPostInitial=0
    tickStrokeThickness=2
    tickStartExtent=0.2
    tickEndExtent=0.075
    minorTickCount=4
    minorTickBrush="DarkViolet"
    minorTickEndExtent=0.1
    minorTickStartExtent=0.2
    minorTickStrokeThickness=1>
</igx-bullet-graph>
```

<div class="sample-container" style="height: 125px">
    <iframe id="bullet-graph-background-iframe" src='{environment:demosBaseUrl}/bullet-graph-background' width="100%" height="100%" seamless frameBorder="0" onload="onSampleIframeContentLoaded(this);"></iframe>
</div>
<div>
    <button data-localize="stackblitz" class="stackblitz-btn"   data-iframe-id="bullet-graph-background-iframe" data-demos-base-url="{environment:demosBaseUrl}">StackBlitz で開く
    </button>
</div>

### スケール
スケールはゲージで値の全範囲を強調表示する視覚的な要素です。外観やスケールの図形のカスタマイズ、更にスケールを反転 (`isScaleInverted` プロパティを使用) させて、すべてのラベルを左から右ではなく、右から左へ描画することもできます。

```html
<igx-bullet-graph
    height="80px" width="400px"
    minimumValue=0 value=70 interval=10
    maximumValue=100 targetValue=90

    isScaleInverted=false
    scaleBackgroundBrush="DodgerBlue"
    scaleBackgroundOutline="DarkViolet"
    scaleBackgroundThickness=2
    scaleStartExtent=0.05
    scaleEndExtent=0.95>
</igx-bullet-graph>
```
<div class="sample-container" style="height: 125px">
    <iframe id="bullet-graph-scale-iframe" src='{environment:demosBaseUrl}/bullet-graph-scale' width="100%" height="100%" seamless frameBorder="0" onload="onSampleIframeContentLoaded(this);"></iframe>
</div>
<div>
    <button data-localize="stackblitz" class="stackblitz-btn"   data-iframe-id="bullet-graph-scale-iframe" data-demos-base-url="{environment:demosBaseUrl}">StackBlitz で開く
    </button>
</div>

### まとめ
上記すべてのコード スニペットを以下のコード ブロックにまとめています。プロジェクトに簡単にコピーしてブレットグラフのすべての機能を再現できます。

```html
<igx-bullet-graph
    height="80px" width="400px"
    minimumValue=0
    maximumValue=100
    isScaleInverted=false
    scaleBackgroundBrush="Gray"
    scaleBackgroundOutline="Gray"
    scaleBackgroundThickness=2
    scaleStartExtent=0.05
    scaleEndExtent=0.95

    value=50
    valueBrush="Black"
    valueStrokeThickness=1
    valueInnerExtent=0.5
    valueOuterExtent=0.65
    targetValue=80
    targetValueBreadth=7.5
    targetValueBrush="Black"
    targetValueOutline="Black"
    targetValueStrokeThickness=1
    targetValueInnerExtent=0.3
    targetValueOuterExtent=0.85

    labelInterval=10
    labelExtent=0.025
    labelsPreTerminal=0
    labelsPostInitial=0
    fontBrush="Black"
    font="11px Verdana"

    backingBrush="#cecece"
    backingOutline="#cecece"
    backingStrokeThickness=4
    backingInnerExtent=0
    backingOuterExtent=1

    interval=10
    tickBrush="Black"
    ticksPreTerminal=0
    ticksPostInitial=0
    tickStrokeThickness=2
    tickStartExtent=0.2
    tickEndExtent=0.075

    minorTickCount=4
    minorTickBrush="Black"
    minorTickEndExtent=0.1
    minorTickStartExtent=0.2
    minorTickStrokeThickness=1

    rangeBrushes ="#C62828, #F96232, #FF9800"
    rangeOutlines="#C62828, #F96232, #FF9800">
    <igx-linear-graph-range
        startValue=20 endValue=40
        innerStartExtent=0.25 innerEndExtent=0.25
        outerStartExtent=0.9 outerEndExtent=0.9>
    </igx-linear-graph-range>
    <igx-linear-graph-range
        startValue=40 endValue=60
        innerStartExtent=0.25 innerEndExtent=0.25
        outerStartExtent=0.9 outerEndExtent=0.9>
    </igx-linear-graph-range>
    <igx-linear-graph-range
        startValue=60 endValue=90
        innerStartExtent=0.25 innerEndExtent=0.25
        outerStartExtent=0.9 outerEndExtent=0.9>
    </igx-linear-graph-range>
</igx-bullet-graph>
```
