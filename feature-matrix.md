---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Feature Matrix

<table><thead><tr><th>Feature</th><th width="67" data-type="checkbox">Status</th><th>Description</th><th>Proposed Syntax</th></tr></thead><tbody><tr><td>Full Properties</td><td>false</td><td>Currently, only auto properties are supported. We need to also add support for defining full properties with a getter and a setter.</td><td><pre><code>property PlayerREF: Actor {
    get { // ... }
    set { // ... }
}
</code></pre></td></tr><tr><td>AutoReadOnly Properties (v1.0.2-alpha.1)</td><td>true</td><td>Add support for AutoReadOnly</td><td><pre><code>auto readonly property PlayerREF: Actor
</code></pre></td></tr><tr><td>Conditional Properties (v1.0.2-alpha.1)</td><td>true</td><td>Add support for Conditional</td><td><pre><code>auto conditional property PlayerREF: Actor
</code></pre></td></tr><tr><td>Various Naive Optimizations</td><td>false</td><td>See <a data-mention href="proposals/naive-optimizations.md">naive-optimizations.md</a></td><td></td></tr><tr><td>Script Flags (v1.0.2-alpha.1)</td><td>true</td><td>Hidden / Conditional</td><td><code>hidden script ...</code> <code>conditional script ...</code></td></tr><tr><td>Variable Flags (v1.0.2-alpha.1)</td><td>true</td><td>Conditional</td><td><code>conditional someBool: Bool = true</code></td></tr><tr><td>Function Flags (v1.0.2-alpha.1)</td><td>true</td><td>Native, Global</td><td><code>native def abc()...</code> <code>global def abc()...</code></td></tr></tbody></table>

