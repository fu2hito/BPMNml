# BPMml[WIP]

[English/英語](./README.md) | Japanese/日本語

BPMmlは、BPMNのマークアップ言語です。文法は当初[Class Digram](https://mermaid.js.org/syntax/classDiagram.html)にインスパイアされました。
[Mermaid](https://mermaid.js.org/)への対応を目指しています。

## Demo

* [BPMml in langium playground](https://langium.org/playground?grammar=OYJwhgthYgBAQgBQLIQDYCgMHpu0P0MgPwyD7DIFMMg1wzmHmB2DIFnaglf4YAuApiBAJYB2YasASQAiALljYA2mAC0ALwCC0gFoB9ALpS5ipQAZpATnUAqbAG4W7Lr34BlACoAlAQDkA4mOwAiABQSAep4AOiCB3GoAlEaeeAA%2B4gDkvn7xwaERRvFmFhw8fILOdrAgrMwAriDcAM6w3KUQAEbsHhJ6%2BmoA1FkYABacACZ9rNywbDnWsADqNh6BlZ3mvQNDI5a5tgAyKgDCAPLIyACiBTPYgZJ%2BocFqJgv9g8OjVnnIm7v7R3YngUb%2BRtff7SS2D%2Bv3%2BRnakTOXVwsEAFQyAZ4ZABMMgCuGajUDBDZggACeCBQzmQAHtBmgRBhYBTYKw0KwIJi5gBeJDIZwHGl07jMIzmHB4ZnOQCBkYACX3oTH5bNpmLJlNgzmJrFgcS2hM5YB47EVsGV3G4rAAxsxOCqeTDAHMMhEAkww0QC9RoBDGMYGDlg2llIOADdMZq7GBKgBrTWuMBsADuYGxJrwgBKGQCbDEjRRh3VLyZT4qwPZz4jVIKwGcJYN54gAeQuZtOYuzYgAOOcTnIr1dg8QAfE34uEAPwR2AxuOAOi9AHoZ8drzHrrBdFMqzBgzFgDMbk%2BnmZiyYpQz6s8ba6XK9gPEerD6nCDCrn8T3lgPR7Y8S7%2BEAnQyAeoZ496-ePG1O-ZneHTc0Iu4AmhkIRFADKGQByhkjeNAxDMM33iYBj1DbEv2zX98yLEtYHg6DsVHBkoNYRDR0bFs207LAYUAkDwJoAdIIQsNRzfVgAA89TQUpKk4D0N1TVj2M4j1txlSsYD4Gl%2BFPETwDQcShMpHg2I4riT0bBT%2BOUm9yLwQBmhnhQAxhlIG17SYbUp3VEA30QQlCX4OJ1jAXUu0AdYZqHjKybNgytrLQZCfzzeIAG94h3GVqUlTlGXFdlMSMHd4gAX003lYEAG4ZCHheN7N1WC0Ac1hfJzfygpCykwo5ZhIvxCVytimUEqSmFAFLjQAs33jbVdQNI1uDfSpCXKPUcwkJ0x2ENQ0OkaRW01eIADoZqmuJ4gmtsRhgYASgZIb5REUa0JETNcsaNAGXsJw3A7cwgA&content=KYN2DsBcAIGVIIYCdIFExWgHiwZ0SgHyEBQiuA1tACoKUCCJA5gpMAO4ICe0AIsAGMAlriEB7cAAUxQzDmAAPAQBsArqLDEydKrUoAhbZRo6AwiVAQYqcABN0V7Fgi2tJeMjQYYAWh%2BETBhI9CnpoPwD%2BYVEJaVlIEiiRcSkZTAjAin1oAC5oACIuYFx8xMFk2LTff0zTXILwMVKQ7Iybe29gs3Ca9ocoEhIABzExZWgAM3xpMegAbxJoJehlBHBgSfwAGTWNheWD6EtMDxQARid8Ty1D5ePrOwAmJxcb27gCSDO2p8XlgF8SP8gA)

## Goal

* [ ] 主要なBPMN仕様に対応
* [ ] Mermaidにマージ
* [ ] BPMN XMLのコード生成

## 内容

```BPMml
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
grammar BPMml

// ターミナルルールの定義
terminal ID: /[a-zA-Z_][a-zA-Z0-9_]*/;
terminal STRING: /"([^"\r\n])*"/ | /'([^'\r\n])*'/;
terminal INT returns number: /[0-9]+/;

hidden terminal WS: /\s+/;
hidden terminal SL_COMMENT: /\/\/[^\n\r]*/;
hidden terminal ML_COMMENT: /\/\*[^*]*\*+([^/*][^*]*\*+)*\//;

// エントリールール
entry BPMNModel:
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
