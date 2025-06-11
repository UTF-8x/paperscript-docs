# Welcome to PaperScript

**PaperScript** is a modern alternative to [Papyrus](https://ck.uesp.net/wiki/Category:Papyrus) that transpiles into valid Papyrus code.

{% hint style="info" %}
PaperScript is in very early stages of development and literally everything is subject to change.
{% endhint %}

### What is PaperScript

PaperScript is a modern scripting language, inspired by C#, Rust and Scala, that transpiles into valid Papyrus code. It's designed from the ground up to be more user-friendly than Papyrus and adds powerful features that Papyrus does not have

### Supported Games

PaperScript currently supports Skyrim SE/AE and Fallout 4.

### What PaperScript is not

* **A standalone scripting language.** When V2 is complete, it should be relatively trivial to implement an interpreter for the AST but for the time being, it's only a tanspiler.
* **A complete replacement for Papyrus** - Yet. The plan is to have V2 compile directly to Papyrus "bytecode" (PEX). This would allow us to drop the intermediate Papyrus step completely and implement more advanced features that Papyrus doesn't support. PEX files are basically just a list of opcodes so the possibilities are quite endless.

### Some Examples

A picture (or a code example) is worth a thousand words so here are some basic examples of PaperScript.

```rust
// PaperScript has a very simple C-like preprocessor
#define DEBUG

script OnEquipHandler : ObjectReference {
    auto property PlayerREF: Actor
    auto property Gold001: MiscItem
    
    event OnEquipped(actor: Actor) {
        PlayerREF.AddItem(Gold001, 10)
        Debug.MessageBox("The magical armor grants you money")
        
        #if DEBUG
        Debug.Notification("gave gold to player")
        #endif
    }
    
    event OnUnequipped(actor: Actor) {
        PlayerREF.RemoveItem(Gold001, 10)
        Debug.MessageBox("The magical armor takes your money")
        
        #if DEBUG
        Debug.Notification("removed money from player")
        #endif
    }
}
```

```rust
#define OUTPUT_FILE_NAME "SomeFunctions.psc"

script SomeFunctions : ObjectReference {
    auto property Gold001: MiscItem

    def VoidWithNoArgs() {
        Debug.MessageBox("Hello World")
    }
    
    def VoidWithArgs(player: Actor, amount: Int) {
        player.AddItem(Gold001, amount)
    }
    
    def BoolWitNoArgs() -> Bool {
        return true
    }
    
    def FloatWithArgs(first: Float, second: Float) -> Float {
        return first + second
    }
}
```
