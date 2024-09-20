# BPMNml [WIP]

[English/英語](./README.md) | Japanese/日本語

BPMNmlは、BPMNのマークアップ言語です。文法は当初[Class Digram](https://mermaid.js.org/syntax/classDiagram.html)にインスパイアされました。
[Mermaid](https://mermaid.js.org/)への対応を目指しています。

## デモ

* [BPMNml in langium playground](https://langium.org/playground?grammar=OYJwhgthYgBAQgBQLIDkIBsBQWD0vYALAF2IAcBnALn2AEtjCBXAIwDoBjAewlwgFMQ0OgBMAtACsKfQcJG4WGLi1wj%2BAN35KyuMmA4BrMMH7S9ICoNwUQHXBjAA7YE2P9c3KF0ceeEb2wOznRMEHgEdBBkXCDEsABEbGy%2BXj6e-o7xANxYdI7EggBm%2BvywAMJ%2B3rAA3liwsPocACKmHCAA-FSwFMQgecA59Y0AKgwY-J3dvf2DsMRjE109fc45AL44heDAAvmwo8TjAIKOIkccHKYUdCx0GAx0plR1sAAUr40tFG0AvEdlZQA%2Bk0AKIAZTKACVYAAfBoXA7jP4AwHDACSwwAMiDYXMFj90ViQQBKWAggDymOJAGosDksFtjLs4hTMbAQPxiEwQI4KFMVsBnvVUCCAOqYtEi6m4ikAMTpOAKQjyYAwsBF4slIK6uAAOh1dT4ckqICq1f8gaCIZCdQBtXVxAC6ACpPq0QK9Ovanc6qK9bQA9Q36l3tT0-ACkEeJMMDwZALpjuoozuq-oDa0Ta2JuGNsjNsAtqIx2LtDtgLpGC29Fd9nqocccIedYfakejsaDTYTzpzeeVjlV%2BxL2tguBrLvmh349YnjebrfbMbnXebML7OEIojUjjm%2BcHatFAAkMeDEP9R%2BPy47qbmsFuRDu9wOhwBNI7ITE6sQ-ifO-XtIas66mCyahgBhrEu0P5iPWEGODCnoAIQgcSG4Pk%2BJoFk0aKQiCZTogAapef5RtU9qgRQoZrFGcEGghyGoeh278LuWEHrAYKSgA4tigISiKgJlOSyDICCqDDGWPpRvOPZ3vgsDpN4OCsb0ACeCAoKgQr1OqYoCSCzovPU8QsGQECOGILCcmA8TGW89kagZzr7AsJxnBcVw3HcDymJpaDIFwagYEZum4k5WouUgAVBVo9lwhFIqhbpxIKuEsAtIUeSlOxQ4gEw4wUFguVqmiTR2mAYgAF5HGIABagKOralU1fVAAMYgAJyNc6d4lZxwyQjxOrxOm8T6oajrEs68QEHCuAAOTpgtE2OFNzoLX1%2B5DpKwzspy3K8rAjihNZIB2h1nU3ne94sWx22HmCOrJre9IKSC%2BQgBp%2BXjFg0WoIFwU6fUWj8MyFDUj8-0guMzLOm9BCZXkDxVFwhT%2BagsCg%2BDf1aTDYOqcD6qxbiFT5GA2VwHCZOOPwHDzN4COFiwyz6HEahZY4KO7mjDTHbFWCoLFRMgpoexwsMYAUAYuLcWABQAO5gGpTNI1zDM8%2BjThY2LxBYKLhP2QtGiqQtx2QPwPxlW8C0ADy22bJv5MMalkJbBvO67pQLQAfD7C1Qar-Cc9zsC807cTEF7RUe8QLtu0TPQwHEPywAtSexGbML2axIiwKnxunFn9l5Ca-AiHQ8ulAXpeyOXlcFAtQchxrYda3MUsGFgkvS0TC3EJ3ZuDgIVtNM3yOt7zYCwMAVdK2pWBy4ryt97Py9qUPFujzb9tm2v-Dz-HltLwfytH2nfsB%2B04-q3QqPo-v89zNHi9z2fXtE-wAAeHAYEw1yaHzmnb%2Bv9-50E0MXMK5hVTjDVAXaBGBYGQN0nkUBADq5p1QX-dBTccAKSOCzXobNYAcwnnfTWfNuDk0plgMmA9KZE0QFwLgao4SYicPwG%2Bocp6wGiCwrATCWF9z4RgTeI9rYLWqAteyYVsaqQhlDPGsNVLJXqAtNYuD0pq24e3II-AsDsNpn3PRYjLYSKkTI3Scj8gKOhso-Iqi04aK4ZPduVDab03IbQ7wHiNaJy4NyS4PxbRCzUFQMqjobY-n9riBaSQYlwgWj%2BAOHcQAmGIME0J-BwlNEia8BaVAzYOGshgH4YJBo8UDkAA&content=LQhQBcEtwGwUwFwAIBCAFAsgOSQZwIYC2ADvKCMKKAEbGEB2w1c4%2BoSHScAbnPeEgDKrAE7gAor35IAPDNyjwAPiXtOrXAGskAFXxaAgmo4BzfODgB3fAE8kAETgBjSLkgB7emneRpcuAAeTjAArm68KsZIGtp6WihRMbr6mgDCUTx8AuL0ACaSWbIyfLmRUcL4YgXSIErJhlFxmgZItQ7Orh5ePvxRji5unt6%2BAm1NKEjIAEQ2cLhTfR2D3SOtwHVNqZNIU-TuC5z1mhNtOflS4I0pW6d51ZdRxO7uMEgAZgreL0gA3lGHMHw9Dg7wUABkgSC-ocYZxMtIKmIAIxFBSVZSqWGw%2BHZPIAJiKJUiWJhAFJSUgsHA4LlcEh8LkAFZhcCEQr6JBOTzApxQTx0yogmCQQjQGnRdzRAAWINwXOIcH%2BWMR4BRt1yeKVHAAvlFtUA)

## Goal

* [ ] 主要なBPMN仕様に対応
* [ ] Mermaidにマージ
* [ ] BPMN XMLのコード生成

## 例

```BPMNml
---
title: BPMN デモ
---

bpmn-beta
    event StartEvent <<start>>
    task TaskA
    gateway DecisionPoint <<exclusive>>
    task TaskB
    task TaskC
    event EndEvent <<end>>

    StartEvent --> TaskA
    TaskA --> DecisionPoint
    DecisionPoint --> TaskB : "yes"
    DecisionPoint --> TaskC : "no"
    TaskB --> EndEvent
    TaskC --> EndEvent

    pool fstPool {
        lane fstLane {
            event Start1 <<start>>
            event End2 <<end>>
            %% コネクションの設定がスコープ内に限定されるため要修正
            Start1 --> End2
        }
    }
```

```langium
grammar BPMNml

// from https://github.com/mermaid-js/mermaid/blob/develop/packages/parser/src/language/common/common.langium
// import "../common/common";
interface Common {
  accDescr?: string;
  accTitle?: string;
  title?: string;
}

fragment TitleAndAccessibilities:
  ((accDescr=ACC_DESCR | accTitle=ACC_TITLE | title=TITLE) EOL)+
;

fragment EOL returns string:
  NEWLINE+ | EOF
;

terminal NEWLINE: /\r?\n/;
terminal ACC_DESCR: /[\t ]*accDescr(?:[\t ]*:([^\n\r]*?(?=%%)|[^\n\r]*)|\s*{([^}]*)})/;
terminal ACC_TITLE: /[\t ]*accTitle[\t ]*:(?:[^\n\r]*?(?=%%)|[^\n\r]*)/;
terminal TITLE: /[\t ]*title(?:[\t ][^\n\r]*?(?=%%)|[\t ][^\n\r]*|)/;

hidden terminal WHITESPACE: /[\t ]+/;
hidden terminal YAML: /---[\t ]*\r?\n(?:[\S\s]*?\r?\n)?---(?:\r?\n|(?!\S))/;
hidden terminal DIRECTIVE: /[\t ]*%%{[\S\s]*?}%%(?:\r?\n|(?!\S))/;
hidden terminal SINGLE_LINE_COMMENT: /[\t ]*%%[^\n\r]*/;
// common

// エントリールール
entry BPMN:
    NEWLINE*
    "bpmn-beta"
    (
    NEWLINE* TitleAndAccessibilities BPMNModel*
    | NEWLINE* BPMNModel
    | NEWLINE*
    )
;

// ターミナルルールの定義
terminal ID: /[a-zA-Z_][a-zA-Z0-9_]*/;
terminal STRING: /"([^"\r\n])*"/ | /'([^'\r\n])*'/;
terminal INT returns number: /[0-9]+/;

hidden terminal WS: /\s+/;

BPMNModel:
    elements+=BPMNElement*;

// BPMN要素の定義
BPMNElement:
    Node | Container | Connection;

// ノードの抽象定義
Node:
    Event | Task | Gateway;

// イベントの定義
Event:
    'event' name=ID ('<<' eventType=EventType '>>')?;

// イベントの種類の定義
EventType:
    start = 'start' |
    end = 'end' |
    intermediate = 'intermediate';

// タスクの定義
Task:
    'task' name=ID;

// ゲートウェイの定義
Gateway:
    'gateway' name=ID ('<<' gatewayType=GatewayType '>>')?;

// ゲートウェイの種類の定義
GatewayType:
    exclusive = 'exclusive' |
    parallel = 'parallel' |
    inclusive = 'inclusive';

// コンテナの抽象定義
Container:
    Pool | Lane;

// プールの定義
Pool:
    'pool' name=ID '{'
        elements+=BPMNElement*
    '}';

// レーンの定義
Lane:
    'lane' name=ID '{'
        elements+=BPMNElement*
    '}';

// 接続の定義
Connection:
    source=[Node:ID] ('-->' | '..>' | '--') target=[Node:ID] (':' label=STRING)?;
```

## 参考

* [Business Process Model and Notation](https://www.omg.org/spec/BPMN)
* [Class diagrams](https://mermaid.js.org/syntax/classDiagram.html)
* [Adding a New Diagram/Chart 📊 | Mermaid](https://mermaid.js.org/community/new-diagram.html)
* [Grammar Language | langium](https://langium.org/docs/reference/grammar-language/)

## ライセンス

[Apache-2.0 license](./LICENSE)
