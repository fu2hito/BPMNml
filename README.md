# BPMml [WIP]

English/英語 | [Japanese/日本語](./README.ja.md)

BPMml is a markup language for BPMN. The syntax was initially inspired by the [Class Diagram](https://mermaid.js.org/syntax/classDiagram.html).
It aims to be compatible with [Mermaid](https://mermaid.js.org/).

## Demo

* [BPMml in langium playground](https://langium.org/playground/?grammar=OYJwhgthYgBAQgBQLIDkIBsBQWD0vZB%2BhkB%2BGQfYZAphkGuGS4ywOwZAs7UEr-LAFwFMQIBLAOzAywAkgBEAXLFwBtMAFoAXgEFZALQD6AXRkLlKgAyyAnJoBUuANxtOPfoIDKAFQBKQ1AHEJuAEQAKKQD0vAB0QIN4NAEoTLwIAH0kAcj9-BJCwyJMEiysuPgFhVAdYEHZWAFcQXgBnWF4yiAAjTk8pA0MNAGpsrAALbgATfvZeWA5c21gAdTtPIKquyz7B4dHrPPsAGTUAYQB5ZGQAUULZ3CDpfzCQjTNFgaGRsZt85C29g%2BOHU6CTAJMbn4dZK4f5-AEmDpRc7dfCwQAVDIBnhkAEwyAK4ZaLQsMNWCAAJ4IFCoZAAeyGGDEWFglNg7Aw7AgWPmAF4kGhDrT6bxWCZLHgCCzUIBAyMABL6MFj8tl0rHkqmwVAk9iweLbImcsB8TiK2DK3i8dgAY1Y3BVPNhgDmGYiASYY6IBeo0AhjHMLByobSqmHABuWM1DjAVQA1pq3GAOAB3MA4k0EQAlDIBNhmRoqw7qlFKpCXYHs5CVqkHYjNEsB8CQAPIXM2msQ4cQAHHOJzkV6uwBIAPibCQiAH4I7AY3HAHRegD0M%2BO11j19guylVVgwViwRmNyfTzOxZOU4b9WeNtdLlewPhPdj9bhBhVzhJ76wHo8cBJdwiAToZAPUM8e9fvHjanfsz-HpuZEXcATQzEEigBlDIA5QyRvGgYhmGb4JMAx6hjiX7Zr%2B%2BZFiWsDwdBOKjoyUHsIho6Ni2badjgsKASB4F0AOkEIWGo5vuwAAeeoYGUVTcB6G6pqx7GcR624ypWMACLSginiJ4AYOJQlUnwbEcVxJ6Ngp-HKTe5EEIAzQwIoAYwzkDa9osNqU7qiAb6IESRKCPEGxgLqXaAOsMtDxlZNmwZW1kYMhP55gkADeCQ7jKNKSpyTLiuyWImDuCQAL6abysCADcMxAIvG9m6rBGAOewvk5v5QUhVSYUcqwkUEhK5WxTKCVJbCgClxoAWb7xtquoGkavBvlURIVHqOZSE6Y6iBoaGyLIraagkAB0M1TfECQTW2owwMApSMkN8piKNaFiJmuVNBgjKOC47gdpYQA&content=KYN2DsBcAIGVIIYCdIFExWgHiwZ0SgHyEBQiuA1tACoKUCCJA5gpMAO4ICe0AIsAGMAlriEB7cAAUxQzDmAAPAQBsArqLDEydKrUoAhbZRo6AwiVAQYqcABN0V7Fgi2tJeMjQYYAWh%2BETBhI9CnpoPwD%2BYVEJaVlIEiiRcSkZTAjAin1oAC5oACIuYFx8xMFk2LTff0zTXILwMVKQ7Iybe29gs3Ca9ocoEhIABzExZWgAM3xpMegAbxJoJehlBHBgSfwAGTWNheWD6EtMDxQARid8Ty1D5ePrOwAmJxcb27gCSDO2p8XlgF8SP8gA)

## Goal

* [ ] Support for Major BPMN spec
* [ ] Merge into Mermaid
* [ ] BPMN XML code generator

## Example

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
        %% Needs adjustment as connections are limited to the scope
        Start1 --> End2
    }
}
```

```langium
grammar BPMml

// Define terminal rules
terminal ID: /[a-zA-Z_][a-zA-Z0-9_]*/;
terminal STRING: /"([^"\r\n])*"/ | /'([^'\r\n])*'/;
terminal INT returns number: /[0-9]+/;

hidden terminal WS: /\s+/;
hidden terminal SL_COMMENT: /\/\/[^\n\r]*/;
hidden terminal ML_COMMENT: /\/\*[^*]*\*+([^/*][^*]*\*+)*\//;

// Entry rule
entry BPMNModel:
    elements+=BPMNElement*;

// Definition of BPMN elements
BPMNElement:
    Node | Container | Connection;

// Abstract definition of a node
Node:
    Event | Task | Gateway;

// Definition of an event
Event:
    'event' name=ID ('<<' eventType=EventType '>>')?;

// Definition of event types
EventType:
    start = 'start' |
    end = 'end' |
    intermediate = 'intermediate';

// Definition of a task
Task:
    'task' name=ID;

// Definition of a gateway
Gateway:
    'gateway' name=ID ('<<' gatewayType=GatewayType '>>')?;

// Definition of gateway types
GatewayType:
    exclusive = 'exclusive' |
    parallel = 'parallel' |
    inclusive = 'inclusive';

// Abstract definition of a container
Container:
    Pool | Lane;

// Definition of a pool
Pool:
    'pool' name=ID '{'
        elements+=BPMNElement*
    '}';

// Definition of a lane
Lane:
    'lane' name=ID '{'
        elements+=BPMNElement*
    '}';

// Definition of a connection
Connection:
    source=[Node:ID] ('-->' | '..>' | '--') target=[Node:ID] (':' label=STRING)?;
```

## References

* [Business Process Model and Notation](https://www.omg.org/spec/BPMN)
* [Class diagrams](https://mermaid.js.org/syntax/classDiagram.html)
* [Adding a New Diagram/Chart 📊 | Mermaid](https://mermaid.js.org/community/new-diagram.html)
* [Grammar Language | langium](https://langium.org/docs/reference/grammar-language/)

## License

[Apache-2.0 license](./LICENSE)
