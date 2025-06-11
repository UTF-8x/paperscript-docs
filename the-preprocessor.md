# The Preprocessor

{% hint style="warning" %}
The PaperScript preprocessor is a very experimental feature and it's really more of a post-processor because it runs after the code is transpiled so keep that in mind...
{% endhint %}

The PaperScript preprocessor works kind of like the C preprocessor but significantly simpler. It only supports a couple features at the moment but there are plans to expand it significantly in the future.

### Defines

You can define a preprocessor variable with `#define` . This variable can then be used in `#if`s and anywhere in your code, where it will be substituted with the value.

Defines can be value-less, in which case the value is set to `true` internally, or valued. Valued defines have a value enclosed in quotes.

```c
#define DEBUG
#define PROJECT_VERSION "1.0.0"
```

### Conditionals

With conditionals, it's possible to include / remove entire blocks of code based on the value of a define. This is very useful for, for example, debug build with more logging.

```c
#define DEBUG

#if DEBUG
Debug.Notification("something happened")
#endif
```

### Substitution

Any mention of a define in your code will be substituted with its value. It's important to give your defines reasonably unique names so you don't accidentally replace something important.

```c
#define PROJECT_NAME "Demo"
#define PROJECT_VERSION "1.0.0"

//...
Debug.Notification("Running PROJECT_NAME version PROJECT_VERSION")
```

### Special Defines

There are some reserved define names that are either used to give additional instructions to the transpiler or set by the CLI internally.

<table><thead><tr><th width="164">Define Name</th><th width="566">Description</th></tr></thead><tbody><tr><td><code>OUTPUT_FILE_NAME</code></td><td>Overrides the output file name for the script it's in.</td></tr><tr><td><code>DEBUG</code></td><td>Can also be set from <code>project.yaml</code> </td></tr><tr><td><code>PROJECT_NAME</code></td><td>Set from <code>project.yaml</code></td></tr><tr><td><code>PROJECT_VERSION</code></td><td>Set from <code>project.yaml</code></td></tr></tbody></table>

## Includes

You can include the contents of a different file.

{% hint style="warning" %}
The include functionality is extremely basic at the moment and included code does not get processed so if you want to include code, it needs to already be Papyrus, not PaperScript. This will be improved in the future.
{% endhint %}

The include path is relative to the file the include is in.

```c
#include "fragment.psc"
```
