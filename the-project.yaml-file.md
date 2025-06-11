# The project.yaml File

```
projectName: New Project
projectVersion: 1.0.0
scriptFolderPath: "Q:/SteamLibrary/steamapps/common/Skyrim Special Edition/Data/Scripts/Source"
scriptOutputPath: "Q:/SteamLibrary/steamapps/common/Skyrim Special Edition/Data/Scripts"
papyrusFlagsPath: "Q:/SteamLibrary/steamapps/common/Skyrim Special Edition/Data/Scripts/Source/TESV_Papyrus_Flags.flg"
papyrusCompilerPath: "Q:/SteamLibrary/steamapps/common/Skyrim Special Edition/Papyrus Compiler/PapyrusCompiler.exe"
sourceGlob: src/**/*.pps
game: SkyrimSE
globalDefines:
  DEBUG: true

```

### projectName

The name of your project

### projectVersion

The version of your project

### scriptFolderPath

The path to your script sources folder

### scriptOutputPath

The path to your compiled scripts folder

### papyrusFlagsPath

The path to your papyrus compiler flags file. This is usually in the script source folder and has a `.flg` extension

### papyrusCompilerPath

Path to the PapyrusCompiler.exe

### sourceGlob

Glob to match your source files. The default will match any `.pps` files in `src/`

### game

Sets the language version. Supported options are `SkyrimSE` and `FO4`&#x20;

### globalDefines

An optional list of defines that will be available in the preprocessor
