# [Gamemakin](https://gamemak.in) Manuale di stile per UE4() {

*Un approccio sufficientemente logico per Unreal Engine 4*

Fortemente ispirato dalla [Airbnb Javascript Style Guide](https://github.com/airbnb/javascript).

[![Analytics](https://ga-beacon.appspot.com/UA-80567399-1/repo?useReferrer)](#)

## Avvisi riguardanti la repository

Questa repository ora si trova su https://github.com/Allar/ue5-style-guide. Il default branch di questa repository è stato rinominato `main`.

## Questo documento è strettamente per UE4. Per UE5/v2, clicka il branch v2
## Linter e documentazione sul manuale di stile

Documentazioni più tecniche riguardanti Linter e il manuale di stile possono essere trovati presso la nostra pagina [ReadTheDocs](https://ue4-style-guide.readthedocs.io/en/latest/).

## Confrontiamoci su questo manuale di stile

Gamemakin LLC ha un canale Discord pubblico presso http://discord.gamemak.in dove all'interno del canale #linter puoi esprimerti riguardo qualsiasi sfaccettatura del manuale di stile e del plugin Linter.

## Come linkare questo documento

Ogni sezione di questo manuale di stile è numerata al fine di ottenere facilità di riferimento e linking. Puoi linkare verso ogni sezione semplicemente aggiungendo un hash tag e il numero di sezione alla fine di http://ue4.style.
Per esempio, se vuoi mandare a qualcuno il primo principio di questo manuale di stile, aggiungi `#0.1` per ottenere http://ue4.style#0.1.

## Fork e traduzioni

Se hai fatto un fork degno di nota o una traduzione che non è adatta per una pull request in questa repo, per favore manda una pull request per aggiungere il fork o la traduzione qui.

* [Traduzione in coreano](https://github.com/ymkim50/ue4-style-guide/blob/master/README_Kor.md) a cura di ymkim50
* [Traduzione in russo](https://github.com/CosmoMyzrailGorynych/ue4-style-guide-rus/blob/master/README.md) a cura di CosmoMyzrailGorynych
* [Traduzione in giapponese](https://github.com/akenatsu/ue4-style-guide/blob/master/README.jp.md) a cura di akenatsu
* [Traduzione in cinese](https://github.com/skylens-inc/ue4-style-guide/blob/master/README.md) a cura di Beijing Skylens Tech
* [Traduzione in portoghese brasiliano](https://github.com/danlvr/ue5-style-guide/blob/main/README_PTBR.md) a cura di danlvr
* [Traduzione in francese](https://github.com/Arnaud58/ue5-style-guide/blob/main/README.md) a cura di Arnaud58

## Indice
- [Terminologia importante](#important-terminology)
  - [Levels/Maps](#terms-level-map)
  - [Identifiers](#terms-identifiers)
  - [Cases](#terms-cases)
  - [Variables / Properties](#terms-var-prop)
    - [Property](#terms-property)
    - [Variable](#terms-variable)
- [0. Princìpi](#0)
  - [0.1 Se il tuo progetto UE4 ha già un manuale di stile, dovresti seguirlo](#0.1)
  - [0.2 Tutte le structure, assets, e codice in qualsiasi progetto Unreal Engine 4 devono apparire come se una singola persona li abbia creati, a prescindere da quante persone abbiano contribuito](#0.2)
  - [0.3 I veri amici non permettono ai loro amici di usare uno stile incoerente](#0.3)
  - [0.4 Un team senza un manuale di stile non è un team di cui voglio far parte](#0.4)
  - [0.5 Non infrangere la legge](#0.5)
- [00. Globally Enforced Opinions](#00)
  - [00.1 Caratteri proibiti](#00.1)
    - [Identifiers](#identifiers)
- [1. Convenzioni nella nominazione degli asset](#anc)
  - [1.1 Nome base dell'asset - `Prefix_BaseAssetName_Variant_Suffix`](#base-asset-name)
    - [1.1 Esempi](#1.1-examples)
  - [1.2 Modifier nel nome degli assets](#asset-name-modifiers)
    - [1.2.1 Più Comuni](#anc-common)
    - [1.2.2 Animations](#anc-animations)
  - [1.2.3 Artificial Intelligence](#anc-ai)
  - [1.2.4 Blueprints](#anc-bp)
  - [1.2.5 Materials](#anc-materials)
  - [1.2.6 Textures](#anc-textures)
    - [1.2.6.1 Texture Packing](#anc-textures-packing)
  - [1.2.7 Miscellaneous](#anc-misc)
  - [1.2.8 Paper 2D](#anc-paper2d)
  - [1.2.9 Physics](#anc-physics)
  - [1.2.10 Sounds](#anc-sounds)
  - [1.2.11 User Interface](#anc-ui)
  - [1.2.12 Effects](#anc-effects)
- [2. Content Directory Structure](#structure)
  - [2e1 Example Project Content Structure](#2e1)
  - [2.1 Folder Names](#structure-folder-names)
    - [2.1.1 Always Use PascalCase](#2.1.1)
    - [2.1.2 Never Use Spaces](#2.1.2)
    - [2.1.3 Never Use Unicode Characters And Other Symbols](#2.1.3)
  - [2.2 Use A Top Level Folder For Project Specific Assets](#structure-top-level)
    - [2.2.1 No Global Assets](#2.2.1)
    - [2.2.2 Reduce Migration Conflicts](#2.2.2)
      - [2.2.2e1 Master Material Example](#2.2.2e1)
    - [2.2.3 Samples, Templates, and Marketplace Content Are Risk-Free](#2.2.3)
    - [2.2.4 DLC, Sub-Projects, and Patches Are Easily Maintained](#2.2.4)
  - [2.3 Use Developers Folder For Local Testing](#structure-developers)
  - [2.4 All Map<sup>*</sup> Files Belong In A Folder Called Maps](#structure-maps)
  - [2.5 Use A `Core` Folder For Critical Blueprints And Other Assets](#structure-core)
  - [2.6 Do Not Create Folders Called `Assets` or `AssetTypes`](#structure-assettypes)
    - [2.6.1 Creating a folder named `Assets` is redundant](#2.6.1)
    - [2.6.2 Creating a folder named `Meshes`, `Textures`, or `Materials` is redundant](#2.6.2)
  - [2.7 Very Large Asset Sets Get Their Own Folder Layout](#structure-large-sets)
  - [2.8 `MaterialLibrary`](#structure-material-library)
  - [2.9 No Empty Folders](#structure-no-empty-folders)
- [3. Blueprints](#bp)
  - [3.1 Compiling](#bp-compiling)
  - [3.2 Variables](#bp-vars)
    - [3.2.1 Naming](#bp-var-naming)
      - [3.2.1.1 Nouns](#bp-var-naming-nouns)
      - [3.2.1.2 PascalCase](#bp-var-naming-case)
        - [3.2.1.2e Examples](#3.2.1.2e)
      - [3.2.1.3 Boolean `b` Prefix](#bp-var-bool-prefix)
      - [3.2.1.4 Boolean Names](#bp-var-bool-names)
        - [3.2.1.4.1 General And Independent State Information](#3.2.1.4.1)
        - [3.2.1.4.2 Complex States](#3.2.1.4.2)
      - [3.2.1.5 Considered Context](#bp-vars-naming-context)
        - [3.2.1.5e Examples](#3.2.1.5e)
      - [3.2.1.6 Do _Not_ Include Atomic Type Names](#bp-vars-naming-atomic)
      - [3.2.1.7 Do Include Non-Atomic Type Names](#bp-vars-naming-complex)
      - [3.2.1.8 Arrays](#bp-vars-naming-arrays)
    - [3.2.2 Editable Variables](#bp-vars-editable)
      - [3.2.2.1 Tooltips](#bp-vars-editable-tooltips)
      - [3.2.2.2 Slider And Value Ranges](#bp-vars-editable-ranges)
    - [3.2.3 Categories](#bp-vars-categories)
    - [3.2.4 Variable Access Level](#bp-vars-access)
      - [3.2.4.1 Private Variables](#bp-vars-access-private)
    - [3.2.5 Advanced Display](#bp-vars-advanced)
    - [3.2.6 Transient Variables](#bp-vars-transient)
    - [3.2.8 Config Variables](#bp-vars-config)
  - [3.3 Functions, Events, and Event Dispatchers](#bp-functions)
    - [3.3.1 Function Naming](#bp-funcs-naming)
    - [3.3.1.1 All Functions Should Be Verbs](#bp-funcs-naming-verbs)
    - [3.3.1.2 Property RepNotify Functions Always `OnRep_Variable`](#bp-funcs-naming-onrep)
    - [3.3.1.3 Info Functions Returning Bool Should Ask Questions](#bp-funcs-naming-bool)
    - [3.3.1.4 Event Handlers and Dispatchers Should Start With `On`](#bp-funcs-naming-eventhandlers)
    - [3.3.1.5 Remote Procedure Calls Should Be Prefixed With Target](#bp-funcs-naming-rpcs)
    - [3.3.2 All Functions Must Have Return Nodes](#bp-funcs-return)
    - [3.3.3 No Function Should Have More Than 50 Nodes](#bp-graphs-funcs-node-limit)
    - [3.3.4 All Public Functions Should Have A Description](#bp-graphs-funcs-description)
    - [3.3.5 All Custom Static Plugin `BlueprintCallable` Functions Must Be Categorized By Plugin Name](#bp-graphs-funcs-plugin-category)
  - [3.4 Blueprint Graphs](#bp-graphs)
    - [3.4.1 No Spaghetti](#bp-graphs-spaghetti)
    - [3.4.2 Align Wires Not Nodes](#bp-graphs-align-wires)
    - [3.4.3 White Exec Lines Are Top Priority](#bp-graphs-exec-first-class)
    - [3.4.4 Graphs Should Be Reasonably Commented](#bp-graphs-block-comments)
    - [3.4.5 Graphs Should Handle Casting Errors Where Appropriate](#bp-graphs-cast-error-handling)
    - [3.4.6 Graphs Should Not Have Any Dangling / Loose / Dead Nodes](#bp-graphs-dangling-nodes)
- [4. Static Meshes](#4)
  - [4.1 Static Mesh UVs](#s-uvs)
    - [4.1.1 All Meshes Must Have UVs](#s-uvs-no-missing)
    - [4.1.2 All Meshes Must Not Have Overlapping UVs for Lightmaps](#s-uvs-no-overlapping)
  - [4.2 LODs Should Be Set Up Correctly](#s-lods)
  - [4.3 Modular Socketless Assets Should Snap To The Grid Cleanly](#s-modular-snapping)
  - [4.4 All Meshes Must Have Collision](#s-collision)
  - [4.5 All Meshes Should Be Scaled Correctly](#s-scaled)
- [5. Niagara](#Niagara)
  - [5.1 No Spaces, Ever](#ng-rules)
- [6. Levels / Maps](#levels)
  - [6.1 No Errors Or Warnings](#levels-no-errors-or-warnings)
  - [6.2 Lighting Should Be Built](#levels-lighting-should-be-built)
  - [6.3 No Player Visible Z Fighting](#levels-no-visible-z-fighting)
  - [6.4 Marketplace Specific Rules](#levels-mp-rules)
    - [6.4.1 Overview Level](#levels-mp-rules-overview)
    - [6.4.2 Demo Level](#levels-mp-rules-demo)
- [7. Textures](#textures)
  - [7.1 Dimensions Are Powers of 2](#textures-dimensions)
  - [7.2 Texture Density Should Be Uniform](#textures-density)
  - [7.3 Textures Should Be No Bigger than 8192](#textures-max-size)
  - [7.4 Textures Should Be Grouped Correctly](#textures-group)