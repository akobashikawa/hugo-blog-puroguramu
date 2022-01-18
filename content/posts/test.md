---
title: "Test"
slug: "test"
summary: "Para probar cosas"
categories: ["Prueba"]
tags: ["prueba", "desarrollo"]
math:
  enable: true
draft: false
outputs:
  - html
  - markdown
hiddenFromHomePage: true
hiddenFromSearch: false
linkToMarkdown: true
date: 2022-01-05T12:42:38-05:00
---

# Heading 1
Párrafo en heading 1

## Heading 2
Párrafo en heading 2

### Heading 3
Párrafo en heading 3

#### Heading 4
Párrafo en heading 4

##### Heading 5
Párrafo en heading 5

###### Heading 6
Párrafo en heading 6

## Lorem

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc quis eros nec mauris lobortis lobortis. Etiam eu lectus lacus. Morbi vitae magna sagittis odio porta feugiat at a mi. Integer ornare egestas erat, et varius ex. Phasellus mauris felis, venenatis quis egestas at, fermentum id purus. Praesent vitae libero vehicula, lacinia tortor vehicula, convallis nibh. Nulla vitae finibus nulla. Maecenas consectetur, mauris at lacinia accumsan, magna nisl consectetur massa, et semper turpis nisi sit amet elit. Duis nec erat dapibus, pretium diam vitae, ornare orci.

## Code

Highlight

```javascript
let sum = function(a, b) {
  return a + v;
}
```

## Gist
{{< gist spf13 7896402 >}}

## Maths

$$ c = \pm\sqrt{a^2 + b^2} $$

## Banners

{{< admonition type=tip title="This is a tip" open=false >}}
A **tip** banner
{{< /admonition >}}

## Flowchart

{{< mermaid >}}
graph LR;
    A[Process] -->|Action| B(Result)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
{{< /mermaid >}}

## Sequence Diagram

{{< mermaid >}}
sequenceDiagram
    participant Alice
    participant Bob
    Alice->>John: Hello John, how are you?
    loop Healthcheck
        John->John: Fight against hypochondria
    end
    Note right of John: Rational thoughts <br/>prevail...
    John-->Alice: Great!
    John->Bob: How about you?
    Bob-->John: Jolly good!
{{< /mermaid >}}

## State Diagram

{{< mermaid >}}
stateDiagram
    [*] --> Still
    Still --> [*]
    Still --> Moving
    Moving --> Still
    Moving --> Near
    Near --> [*]
{{< /mermaid >}}

## Typeit

{{< typeit >}}
This is a *paragraph* with **typing animation** based on [TypeIt](https://typeitjs.com/)...
{{< /typeit >}}

## Instagram

{{< instagram BWNjjyYFxVx >}}