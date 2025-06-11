# Syntax Reference

### Script Block

A script is contained in a `script` block. This is equivalent to `ScriptName extends...` in Papyrus. The only thing that can go before a `script` block are comments and defines.

```rust
#define HELLO_WORLD

// The colon replaces the "extends"
script Demo : ObjectReference {}
```

### Properties

A property is a script-scoped variable that's available to external scripts. A property itself does not actually store anything, it's an interface between a script's private variable and the outside world.

```csharp
_player: Actor = None // a private variable

property Player: Actor {
    get {
        return _player
    }
    
    set {
        _player = value // value is a special variable that refers to the setter value
    }
}
```

### Auto Properties

Auto properties represent a private variable and a basic setter like the one above. An auto property starts with `auto property` and then follows the regular variable format. They can optionally have a default value.

```rust
auto property PlayerREF: Actor
auto property Interval: Float = 1.0
```

### Variables

Variable definitions begin with a name, followed by a type and finally an optional value. Since Papyrus doesn't do type inference, types must be explicitly defined. (Type inference is a future planned feature of PaperScript)

{% hint style="info" %}
See the [Papyrus Variable Reference](https://ck.uesp.net/wiki/Variable_Reference) for more details
{% endhint %}

If you don't specify a value, the variable will be filled with the Papyrus default for that type.

```rust
someBool: Bool = true
someInt: Int = 1

// Defaults
defaultBool: Bool // = false
defaultInt: Int // = 0
defaultFloat: Float // = 0.0
defaultString: String // = ""
defaultaRrray: Int[] // = None
someNullActor: Actor // = None

```

### Functions

A function starts with `def`, has a name, optional arguments and an optional return type. Functions that don't have a return type (`void`), don't need to specify one.

```rust
def HelloWorld() {
  Debug.Notification("Hello World")
}

def ReturnsFloat() -> Float {
  return 1.0
}

def HasArgs(message: String) {
  Debug.Notification(message)
}

def ArgsAndReturn(a: Bool, b: Bool) -> Bool {
  return a | b
}
```

### Events

Events work the same as functions but start with `event` instead of `def` and never have a return type.

```rust
event OnEquipped(actor: Actor) {}
event OnInit() {}
```

### Conditionals

The If/ElseIf/Else syntax is virtually identical to Papyrus but with braces. Parentheses are optional and only used to denote precedence.

{% hint style="danger" %}
`elseif` does not work correctly as of `v1.0.1-alpha.1` , this is a known issue that will be fixed
{% endhint %}

```rust
if a == b {
    // ...
} elseif a == c {
  // ...
} else {
  // ...
}
```

### While

The `while` syntax is the same as Papyrus but with braces. Parentheses are once again optional and used for precedence.

```rust
while someCondition {
  // ...
}
```

### Switch

A `switch` is one of the features sorely missing from Papyrus. PaperScript supports `switch` statements that get translated into if/elseif/else in the resulting Papyrus.

Cases can be single-line or multi-line. Single-line cases must end with a semicolon. Multi-line cases are in braces.

The default case follows the same pattern and will match anything that doesn't have a case.

Cases do not fall through and there is no `break`&#x20;

{% hint style="warning" %}
`switch` is a PaperScript feature with no native equivalent in Papyrus and may not work correctly in some edge cases.

Check out [feature-deep-dive.md](feature-deep-dive.md "mention") to see how this works
{% endhint %}

```rust
switch someVar {
    case 1 => Debug.Notification("1");
    case 2 => {
      Debug.Notification("2")
    }
    default => Debug.Notification("default");
}
```

### Range

`range` is another new addition to PaperScript that doesn't exist in Papyrus. It works as a `foreach` loop and gets translated into a while in the resulting Papyrus.

{% hint style="warning" %}
`range` is a PaperScript feature with no native equivalent in Papyrus and may not work correctly in some edge cases.

Check out [feature-deep-dive.md](feature-deep-dive.md "mention") to see how this works
{% endhint %}

```rust
range item in items {
  DoSomething(item)
}
```

