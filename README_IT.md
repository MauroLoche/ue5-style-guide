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

Nota della traduzione italiana: parla della scelta di quali termini tradurre e quali no per facilitare indicizzazione e fruibilità.

Al fine di facilitare l'indicizzazione e la fruibilità del documento ho preferito mantenere in inglese i termini tecnici. L'idea è che questo documento sia tra i primi a cui uno sviluppatore poco avvezzo alla lingua inglese si affidi, esponendolo però immediatamente ai termini tecnici inglesi. La traduzione di questi termini se necessaria è presente in Internet e vi invito a cercarle nel caso abbiate serie difficoltà a capire il documento; sappiate però che in un team di sviluppo o se avete bisogno di googlare risposte, le terminologie inglesi saranno NECESSARIE per ottenere dei risultati.

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
    - [1.2.1 I più comuni](#anc-common)
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
- [2. Struttura della directory dei contenuti](#structure)
  - [2e1 Example Project Content Structure](#2e1)
  - [2.1 Folder Names](#structure-folder-names)
    - [2.1.1 Usa sempre PascalCase](#2.1.1)
    - [2.1.2 Non usare mai la barra spaziatrice](#2.1.2)
    - [2.1.3 Non usare mai caratteri Unicode e altri symboli](#2.1.3)
  - [2.2 Usa una cartella Top Level per assets Project Specific](#structure-top-level)
    - [2.2.1 No assets per uso globale](#2.2.1)
    - [2.2.2 Riduci i conflitti delle Migration](#2.2.2)
      - [2.2.2e1 Esempio di Master Material](#2.2.2e1)
    - [2.2.3 Samples, Templates, and Marketplace Content sono sicuri e senza rischi](#2.2.3)
    - [2.2.4 DLC, sottoprogetti e patches sono di facile manutenzione](#2.2.4)
  - [2.3 Usa la cartella Developers Folder per effettuare Local Testing](#structure-developers)
  - [2.4 Tutti i Map<sup>*</sup> file appartengono ad una cartella chiamata Maps](#structure-maps)
  - [2.5 Usa una cartella `Core` per Blueprints di alta importanza e altri Assets](#structure-core)
  - [2.6 Non creare cartelle chiamate `Assets` o `AssetTypes`](#structure-assettypes)
    - [2.6.1 Creare una cartella chiamata `Assets` è ridondante](#2.6.1)
    - [2.6.2 Creare una cartella chiamata `Meshes`, `Textures`, or `Materials` è ridondante](#2.6.2)
  - [2.7 Very Large Asset Sets hanno un loro proprio layout di cartella](#structure-large-sets)
  - [2.8 `MaterialLibrary`](#structure-material-library)
  - [2.9 Mai cartelle vuote](#structure-no-empty-folders)
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
        - [3.2.1.5e esempi](#3.2.1.5e)
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
    - [3.3.1.1 Tutte le Functions Should Be Verbs](#bp-funcs-naming-verbs)
    - [3.3.1.2 Property RepNotify Functions Always `OnRep_Variable`](#bp-funcs-naming-onrep)
    - [3.3.1.3 Info Functions Returning Bool Should Ask Questions](#bp-funcs-naming-bool)
    - [3.3.1.4 Event Handlers and Dispatchers Should Start With `On`](#bp-funcs-naming-eventhandlers)
    - [3.3.1.5 Remote Procedure Calls Should Be Prefixed With Target](#bp-funcs-naming-rpcs)
    - [3.3.2 Tutte le Functions devono avere Return Nodes](#bp-funcs-return)
    - [3.3.3 Nessuna Function dovrebbe avere più di 50 Nodes](#bp-graphs-funcs-node-limit)
    - [3.3.4 All Public Functions dovrebbero avere una descrizione](#bp-graphs-funcs-description)
    - [3.3.5 All Custom Static Plugin `BlueprintCallable` Functions Must Be Categorized By Plugin Name](#bp-graphs-funcs-plugin-category)
  - [3.4 Blueprint Graphs](#bp-graphs)
    - [3.4.1 No Spaghetti](#bp-graphs-spaghetti)
    - [3.4.2 Align Wires Not Nodes](#bp-graphs-align-wires)
    - [3.4.3 White Exec Lines Are Top Priority](#bp-graphs-exec-first-class)
    - [3.4.4 Graphs dovrebbero essere sufficientemente commentati](#bp-graphs-block-comments)
    - [3.4.5 Graphs dovrebbero Handle Casting Errors Where Appropriate](#bp-graphs-cast-error-handling)
    - [3.4.6 Graphs non dovrebbero avere nessun tipo di nodo  Dangling / Loose / Dead ](#bp-graphs-dangling-nodes)
- [4. Static Meshes](#4)
  - [4.1 Static Mesh UVs](#s-uvs)
    - [4.1.1 Tutte le Meshes devono avere UVs](#s-uvs-no-missing)
    - [4.1.2 Tutte le Meshes non devono avere Overlapping UVs for Lightmaps](#s-uvs-no-overlapping)
  - [4.2 LODs Should Be Set Up Correctly](#s-lods)
  - [4.3 Gli assets Modular Socketless dovrebbero Snap To The Grid Cleanly](#s-modular-snapping)
  - [4.4 Tutte le Meshes devono avere collisione](#s-collision)
  - [4.5 Tutte le meshes devono essere in scala corretta](#s-scaled)
- [5. Niagara](#Niagara)
  - [5.1 Mai usare la barra spaziatrice](#ng-rules)
- [6. Levels / Maps](#levels)
  - [6.1 Mai errori o warnings](#levels-no-errors-or-warnings)
  - [6.2 La lighting dovrebbe essere Built](#levels-lighting-should-be-built)
  - [6.3 No Player Visible Z Fighting](#levels-no-visible-z-fighting)
  - [6.4 Regole specifiche del Marketplace](#levels-mp-rules)
    - [6.4.1 Overview livello](#levels-mp-rules-overview)
    - [6.4.2 Livello demo](#levels-mp-rules-demo)
- [7. Textures](#textures)
  - [7.1 Dimensions Are Powers of 2](#textures-dimensions)
  - [7.2 Texture Density dovrebbe essere uniforme](#textures-density)
  - [7.3 Textures non dovrebbero essere più grandi di 8192](#textures-max-size)
  - [7.4 Textures dovrebbero essere raggruppate correttamente](#textures-group)

## Important Terminology

<a name="terms-level-map"></a>
##### Levels/Maps

La parola 'map' generally si riferisce genericamente a ciò che una persona qualsiasi chiama 'level' e può essere usato in maniera interscambiabile. Controlla la storia di questo termine [qui](https://en.wikipedia.org/wiki/Level_(video_gaming)).

<a name="terms-identifiers"></a>
##### Identifiers
Un `Identifier` is anything that resembles or serves as a "name". Per esempio, il nome di un asset, o il nome di un material later, o una proprietà del blueprint, una variable, o il nome di una cartella, or for a data table row name, ecc...

<a name="terms-cases"></a>
##### Cases

There are a few different ways you can `CaseWordsWhenNaming`. Here are some common casing types:

> ###### PascalCase
>
> Capitalize ogni parola e rimuovi tutti gli spazi, e.g. `DesertEagle`, `StyleGuide`, `ASeriesOfWords`.
>
> ###### camelCase
>
> La prima lettera è sempre minuscola ma ogni parola seguente inizia con un maiuscolo, e.g. `desertEagle`, `styleGuide`, `aSeriesOfWords`.
>
> ###### Snake_case
>
> Words can arbitrarily start upper or lowercase but words are separated by an underscore, e.g. `desert_Eagle`, `Style_Guide`, `a_Series_of_Words`.

<a name="terms-var-prop"></a>
##### Variables / Properties

The words 'variable' and 'property' nella maggior parte dei contesti sono intercambiabili. Tuttavia, se sono usate entrambe nello stesso contesto/frase:

<a name="terms-property"></a>
###### Property
In genere ci si riferisce a una variable definita in una class. Per esempio, se `BP_Barrel` had a variable `bExploded`, `bExploded` may be referred to come una proprietà di `BP_Barrel`.

When in the context of a class, é usato spesso per implicare l'accesso a data definito precedentemente.

<a name="terms-variable"></a>
###### Variable
In genere refers a una variable definita come una function argument o una local variable dentro una function.

Nel contesto di una class, è spesso usato per convogliare dialogo riguardo la sua definition e cosa questa conterrà.

<a name="0"></a>
## 0. Principles

Questi principles sono stati adattati da [idomatic.js style guide](https://github.com/rwaldron/idiomatic.js/).

<a name="0.1"></a>
### 0.1 Se il tuo progetto UE4 ha già un manuale di stile, dovresti seguirlo

Se stai lavorando a un progetto da solo o con un team che ha già un manuale di stile pre-esistente, dovresti rispettarlo. Qualsiasi inconsistenza tra un manuale di stile già esistente questa guida e quella già presente cede, dando priorità al manuale di stile scelto dall'azienda.

I manuali di stile dovrebbero essere documenti viventi. Dovresti proporre cambi ad esso e a questa guida se ritieni che attraverso il cambiamento tutti ne possano trarre vantaggio.

> #### "Arguments over style non hanno senso. ci dovrebbe essere soltanto una style guide, e tu la devi seguire."
> [_Rebecca Murphey_](https://rmurphey.com)

<a name="0.2"></a>
### 0.2 Tutte le structure, assets, e codice in qualsiasi progetto Unreal Engine 4 devono apparire come se una singola persona li abbia creati, a prescindere da quante persone abbiano contribuito

Moving from one project to another should not cause a re-learning of stile e struttura. Conforming to a style guide rimuove unneeded guesswork e ambiguità.

It also allows for more productive creation and manutenzione perché nessuno deve spendere ulteriore tempo sullo stile. Semplicemente segui le istruzioni. Questo manuale di stile  guide é stato stilato tenendo conto delle best practices, con il vantaggio che se segui questa style guide renderai più semplice risolvere problemi difficili da rintracciare.