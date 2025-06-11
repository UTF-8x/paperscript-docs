# Quick Start Guide

This short guide will walk you through setting up PaperScript, initializing a project and building your first script.

#### Requirements

* A working install of PaperScript (see [installing.md](paperscript-cli/installing.md "mention"))
* A working copy of Skyrim SE/AE and CreationKit. Make sure to run CK before starting so the script sources get copied.
* A copy of the Papyrus Compier. This should get installed automatically with CK.
* A text exitor. We recommend Visual Studio Code with the PaperScript [vscode-extension.md](vscode-extension.md "mention").

### Creating a New Project

Create a folder to store your project and run `paperscript init` in that folder. This will generate a `project.yaml` for you.

{% hint style="info" %}
The project initializer can detect where Skyrim is installed and set all paths automatically but it needs to run as Administrator to do this.
{% endhint %}

Afterwards, open the `project.yaml` file, fill in your project name and version and make sure all paths are set correctly.

### Write Some Code

Create a file in the `src/` directory with a `.pps` extension and write some PaperScript code. See [syntax-reference.md](syntax-reference.md "mention") for a full reference.

Here is a minimal example:

```
script HelloWorldQuest : Quest {
  auto property PlayerREF: Auto
  auto property Gold001: MiscItem
  
  event OnInit() {
    RegisterForSingleUpdate()
  }
  
  event OnUpdate() {
    GiveGoldToActor(PlayerREF, 10)
  }
  
  def GiveGoldToActor(actor: Actor, amount: Int) {
    actor.AddItem(Gold001, amount)
  }
}
```

### Compile your Code

For the first run, it's usually a good idea to run a one-off build to make sure everything works correctly. To do so, run `paperscript build` .

When you're sure everything is configured correctly, you can run PaperScript in watch mode, where it will automatically recompile any changed files in your project. You can run PaperScript in watch mode with `paperscript watch`.

{% hint style="danger" %}
Watch mode is not implemented yet but it is coming soon.
{% endhint %}

### And that's it!

You should now have a fully functional PaperScript project. Happy coding!
