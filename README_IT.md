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

<a name="0.3"></a>
### 0.3 I veri amici non permettono ai loro amici di usare uno stile incoerente

Se noti qualcuno lavorare senza rispettare un manuale di stile o senza averne uno, cerca di mostrargli la retta via.

Quando si lavora in un team o si discute in una community come quella degli [Unreal Slackers](http://join.unrealslackers.org/), é più facile aiutare e chiedere aiuto quando tutti sono coerenti nella forma. A nessuno piace srotolare il groviglio causato dai nodi dei blueprint di qualcun'altro o avere a chie fare on assets che hanno nomi che non hanno un criterio logico.

Se stai aiutando qualcuno che sta usando un manuale di stile appropriato per il suo lavoro ma diverso dal tuo, sta a te adattarti.Se non hanno uno stanard di style guide, per favore indirizzali qui.

<a name="0.4"></a>
### 0.4 Un team senza un manuale di stile non è un team di cui voglio far parte

When joining an Unreal Engine 4 team, one of your first questions should be "Do you have a style guide?". If the answer is no, you should be skeptical about their ability to work as a team.

<a name="0.5"></a>
### 0.5 Non infrangere la legge

Gamemakin LLC non è un avvocato, ma per favore evita di compiere azioni e behavior illegali al progetto, includendo ma non limitato a:

* Non distribuire content di cui non possiedi diritti di distribuzione
* Non infriengere il diritto di copia altrui, nemmeno nei materiali con trademark
* Non rubare content
* Rispetta le restrizioni di licenza del content, i.e. attribuisci dove l'attribuzione é richiesta

<a name="00"></a>
## 00. Globally Enforced Opinions

@TODO: Make this section 1 and update this document accordingly. Or maybe we don't?

<a name="00.1"></a>
### 00.1 Caratteri vietati

<a name="identifiers-1"></a>
#### Identifiers

In ogni `Identifier` di ogni tipo, non usare **mai** i seguenti a meno che tu non sia forzato:

* White space of any kind
* Backward slashes `\`
* Simboli i.e. `#!@$%`
* Qualsiasi carattere Unicode

Qualsiasi `Identifier` dovrebbe avere solo i seguenti caratteri quando possibile (the RegEx `[A-Za-z0-9_]+`)

* ABCDEFGHIJKLMNOPQRSTUVWXYZ
* abcdefghijklmnopqrstuvwxyz
* 1234567890
* _ (raramente)

Il ragionamento dietro ciò é che questo assicura la maggior compatibilità di tutti i data tra le piattaforme attraverso tutti i tool, e di conseguenza aiuta a prevenire downtime causati da bad character handling per identifiers in codice dove tu non hai controllo.

<a name="anc"></a>
<a name="1"></a>
## 1. Asset Naming Conventions

Naming conventions devono essere trattate come legge. Un progetto che rispetta una naming convention é in grado di avere i propri assets managed, searched, parsed, and maintained con incredibile faciità.

La maggior parte delle cose sono prefissate seguendo una logica dove il prefisso é un acronimo del tipo di asset susseguito da un underscore.

<a name="base-asset-name"></a>
<a name="1.1"></a>
### 1.1 Base Asset Name - `Prefix_BaseAssetName_Variant_Suffix`

Tutti gli assets dovrebbero avere un _Base Asset Name_. Un Base Asset Name rappresenta un raggruppamento logico di related assets. Qualsiasi asset che fa parte di questo gruppo logico dovrebbe seguire lo standard di `Prefix_BaseAssetName_Variant_Suffix`.

Rispettare il pattern `Prefix_BaseAssetName_Variant_Suffix`, tenerlo a mente e usare il buonsenso é genericamente abbastanza per garantire degli asset name buoni. Qui sotto trovi regole più dettagliate riguardanti ogni elemento.

`Prefix` e `Suffix` si determinano dal tipo di asset attraverso le seguenti [Asset Name Modifier](#asset-name-modifiers) tabelle.

`BaseAssetName` dovrebbe essere scelto attraverso un nome breve e facilmente riconoscibile riguardante il contesto di questo gruppo di assets. Per eempio, se hai un personaggio di nome Bob, tutti gli asset di Bob dovrebbero avere il `BaseAssetName` di `Bob`.

Per uniche e specifiche variazioni di assets, `Variant` é un nome breve e facilmente riconoscibile che rappresenta raggruppamento logico di assets che sono un subset del nome base dell'asset principale. Per esempio, se Bob avesse varie skin, queste dovrebbero usare sempre `Bob` come `BaseAssetName` ma inoltre includere una riconoscibile `Variant`. Una skin 'da arcinemico' dovrebbe essere chiamata `Bob_Evil` e una skin con lo stile 'Retro' si dovrebbe chiamare `Bob_Retro`.

Per variazioni di assets generiche ma uniche, `Variant` é un numero di due cifre che parte da `01`. Per esempio, se hai un environment artist che ha generato rocce nondescript, dovrebbero essere nominate `Rock_01`, `Rock_02`, `Rock_03`, etc. Ad eccezione di casi rarissimi, non dovresti mai aver bisogno di variant da tre cifre. Se hai più di 100 assets, dovresti tener in conto di riorganizzarle con base names diversi o usare un maggior numero di variant names.

A seconda di come i tuoi asset variants sono fatti, puoi concatenare assieme variant names. Per esempio, se stai creando flooring assets per un progetto Arch Viz, dovresti usare il base name `Flooring` con varianti concatenate come per esempio `Flooring_Marble_01`, `Flooring_Maple_01`, `Flooring_Tile_Squares_01`.

<a name="1.1-examples"></a>
#### 1.1 Examples

##### 1.1e1 Bob

| Tipo di asset              | Nome dell'asset                                                |
| ----------------------- | ---------------------------------------------------------- |
| Skeletal Mesh           | SK_Bob                                                     |
| Material                | M_Bob                                                      |
| Texture (Diffuse/Albedo)| T_Bob_D                                                    |
| Texture (Normal)        | T_Bob_N                                                    |
| Texture (Evil Diffuse)  | T_Bob_Evil_D                                               |

##### 1.1e2 Rocks

| Tipo di asset              | Nome dell'asset                                                 |
| ----------------------- | ---------------------------------------------------------- |
| Static Mesh (01)        | S_Rock_01                                                  |
| Static Mesh (02)        | S_Rock_02                                                  |
| Static Mesh (03)        | S_Rock_03                                                  |
| Material                | M_Rock                                                     |
| Material Instance (Snow)| MI_Rock_Snow                                               |

<a name="asset-name-modifiers"></a>
<a name="1.2"></a>
### 1.2 Asset Name Modifiers

Quando dai il nome a un asset, usa queste tabelle per determinare il prefisso e il suffisso da usare  con il [Base Asset Name](#base-asset-name) di quell'asset.

<a name="anc-common"></a>
<a name="1.2.1"></a>
#### 1.2.1 Most Common

| Tipo di asset              | Prefix     | Suffisso     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Level / Map             |            |            | [Should be in a folder called Maps.](#2.4) |
| Level (Persistent)      |            | _P         |                                  |
| Level (Audio)           |            | _Audio     |                                  |
| Level (Lighting)        |            | _Lighting  |                                  |
| Level (Geometry)        |            | _Geo       |                                  |
| Level (Gameplay)        |            | _Gameplay  |                                  |
| Blueprint               | BP_        |            |                                  |
| Material                | M_         |            |                                  |
| Static Mesh             | S_         |            | Many use SM_. We use S_.         |
| Skeletal Mesh           | SK_        |            |                                  |
| Texture                 | T_         | _?         | See [Textures](#anc-textures)    |
| Particle System         | PS_        |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-animations"></a>
<a name="1.2.2"></a>
#### 1.2.2 Animations

| Tipo di asset              | Prefix     | Suffisso     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Aim Offset              | AO_        |            |                                  |
| Aim Offset 1D           | AO_        |            |                                  |
| Animation Blueprint     | ABP_       |            |                                  |
| Animation Composite     | AC_        |            |                                  |
| Animation Montage       | AM_        |            |                                  |
| Animation Sequence      | A_         |            |                                  |
| Blend Space             | BS_        |            |                                  |
| Blend Space 1D          | BS_        |            |                                  |
| Level Sequence          | LS_        |            |                                  |
| Morph Target            | MT_        |            |                                  |
| Paper Flipbook          | PFB_       |            |                                  |
| Rig                     | Rig_       |            |                                  |
| Skeletal Mesh           | SK_        |            |                                  |
| Skeleton                | SKEL_      |            |                                  |

<a name="anc-ai"></a>
<a name="1.2.3"></a>
### 1.2.3 Artificial Intelligence

| Tipo di asset              | Prefisso     | Suffisso     | Note                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| AI Controller           | AIC_       |            |                                  |
| Behavior Tree           | BT_        |            |                                  |
| Blackboard              | BB_        |            |                                  |
| Decorator               | BTDecorator_ |          |                                  |
| Service                 | BTService_ |            |                                  |
| Task                    | BTTask_    |            |                                  |
| Environment Query       | EQS_       |            |                                  |
| EnvQueryContext         | EQS_       | Dato dal contesto    |                                  |

<a name="anc-bp"></a>
<a name="1.2.4"></a>
### 1.2.4 Blueprints

| Tipo di asset              | Prefisso     | Suffisso     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Blueprint               | BP_        |            |                                  |
| Blueprint Component     | BP_        | Component  | I.e. BP_InventoryComponent       |
| Blueprint Function Library | BPFL_   |            |                                  |
| Blueprint Interface     | BPI_       |            |                                  |
| Blueprint Macro Library | BPML_      |            | Do not use macro libraries if possible. |
| Enumeration             | E          |            | No underscore.                   |
| Structure               | F or S     |            | No underscore.                   |
| Tutorial Blueprint      | TBP_       |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-materials"></a>
<a name="1.2.5"></a>
### 1.2.5 Materials

| Tipo di asset                    | Prefisso     | Suffisso     | Notes                            |
| ----------------------------- | ---------- | ---------- | -------------------------------- |
| Material                      | M_         |            |                                  |
| Material (Post Process)       | PP_        |            |                                  |
| Material Function             | MF_        |            |                                  |
| Material Instance             | MI_        |            |                                  |
| Material Parameter Collection | MPC_       |            |                                  |
| Subsurface Profile            | SP_        |            |                                  |
| Physical Materials            | PM_        |            |                                  |
| Decal                         | M_, MI_    | _Decal     |                                  |

<a name="anc-textures"></a>
<a name="1.2.6"></a>
### 1.2.6 Textures

| Tipo di asset              | Prefisso     | Suffisso     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Texture                 | T_         |            |                                  |
| Texture (Diffuse/Albedo/Base Color)| T_ | _D      |                                  |
| Texture (Normal)        | T_         | _N         |                                  |
| Texture (Roughness)     | T_         | _R         |                                  |
| Texture (Alpha/Opacity) | T_         | _A         |                                  |
| Texture (Ambient Occlusion) | T_     | _O         |                                  |
| Texture (Bump)          | T_         | _B         |                                  |
| Texture (Emissive)      | T_         | _E         |                                  |
| Texture (Mask)          | T_         | _M         |                                  |
| Texture (Specular)      | T_         | _S         |                                  |
| Texture (Metallic)      | T_         | _M         |                                  |
| Texture (Packed)        | T_         | _*         | See notes below about [packing](#anc-textures-packing). |
| Texture Cube            | TC_        |            |                                  |
| Media Texture           | MT_        |            |                                  |
| Render Target           | RT_        |            |                                  |
| Cube Render Target      | RTC_       |            |                                  |
| Texture Light Profile   | TLP        |            |                                  |

<a name="anc-textures-packing"></a>
<a name="1.2.6.1"></a>
#### 1.2.6.1 Texture Packing
È common practice to pack multipli layers di texture data in una texture. Un esempio é il packing dell' Emissive, Roughness, Ambient Occlusion assieme attraverso i canali rosso, verde e blu di una texture respectively. Per determinare il suffisso, semplicemente somma le lettere di suffisso sopra indicate, i.e. `_ERO`.

> È generalmente accettabile includere un layer Alpha/Opacity layer nel tuo alpha channel del Diffuse/Albedo e, siccome é pratica comunie, aggiungere `A` al suffisso `_D` é opzionale.

Unire/ fare Packing 4 channels di data in una texture (RGBA) non é raccomandato, tranne nel solo caso dove una mask Alpha/Opacity nel canale alpha nel Diffuse/Albedo poichè una texture con un alpha channel incurs more overhead rispetto a uno senza.

<a name="anc-misc"></a>
<a name="1.2.7"></a>
### 1.2.7 Miscellaneous

| Tipo di asset                 | Prefisso     | Suffisso     | Note                            |
| -------------------------- | ---------- | ---------- | -------------------------------- |
| Animated Vector Field      | VFA_       |            |                                  |
| Camera Anim                | CA_        |            |                                  |
| Color Curve                | Curve_     | _Color     |                                  |
| Curve Table                | Curve_     | _Table     |                                  |
| Data Asset                 | *_         |            | Il prefisso dovrebbe essere basato sulla class. |
| Data Table                 | DT_        |            |                                  |
| Float Curve                | Curve_     | _Float     |                                  |
| Foliage Type               | FT_        |            |                                  |
| Force Feedback Effect      | FFE_       |            |                                  |
| Landscape Grass Type       | LG_        |            |                                  |
| Landscape Layer            | LL_        |            |                                  |
| Matinee Data               | Matinee_   |            |                                  |
| Media Player               | MP_        |            |                                  |
| File Media Source          | FMS_       |            |                                  |
| Object Library             | OL_        |            |                                  |
| Redirector                 |            |            | Devono essere risolti IL PRIMA POSSIBILE.   |
| Sprite Sheet               | SS_        |            |                                  |
| Static Vector Field        | VF_        |            |                                  |
| Substance Graph Instance   | SGI_       |            |                                  |
| Substance Instance Factory | SIF_       |            |                                  |
| Touch Interface Setup      | TI_        |            |                                  |
| Vector Curve               | Curve_     | _Vector    |                                  |

<a name="anc-paper2d"></a>
<a name="1.2.8"></a>
### 1.2.8 Paper 2D

| Tipo di asset              | Prefisso     | Suffisso     | Note                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Paper Flipbook          | PFB_       |            |                                  |
| Sprite                  | SPR_       |            |                                  |
| Sprite Atlas Group      | SPRG_      |            |                                  |
| Tile Map                | TM_        |            |                                  |
| Tile Set                | TS_        |            |                                  |

<a name="anc-physics"></a>
<a name="1.2.9"></a>
### 1.2.9 Physics

| Tipo di asset              | Prefisso     | Suffisso     | Note                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Physical Material       | PM_        |            |                                  |
| Physics Asset           | PHYS_      |            |                                  |
| Destructible Mesh       | DM_        |            |                                  |

<a name="anc-sounds"></a>
<a name="1.2.10"></a>
### 1.2.10 Sounds

| Tipo di asset              | Prefisso     | Suffisso     | Note                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Dialogue Voice          | DV_        |            |                                  |
| Dialogue Wave           | DW_        |            |                                  |
| Media Sound Wave        | MSW_       |            |                                  |
| Reverb Effect           | Reverb_    |            |                                  |
| Sound Attenuation       | ATT_       |            |                                  |
| Sound Class             |            |            | Nessun prefisso nè suffisso. Dovrebbe essere posto in una catella chiamata SoundClasses |
| Sound Concurrency       |            | _SC        | Il nome dovrebbe essere derivante di quello della sua SoundClass |
| Sound Cue               | A_         | _Cue       |                                  |
| Sound Mix               | Mix_       |            |                                  |
| Sound Wave              | A_         |            |                                  |

<a name="anc-ui"></a>
<a name="1.2.11"></a>
### 1.2.11 User Interface

| Tipo di asset              | Prefisso     | Suffisso     | Note                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Font                    | Font_      |            |                                  |
| Slate Brush             | Brush_     |            |                                  |
| Slate Widget Style      | Style_     |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-effects"></a>
<a name="1.2.12"></a>
### 1.2.12 Effects

| Tipo di asset              | Prefisso     | Suffisso     | Note                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Particle System         | PS_        |            |                                  |
| Material (Post Process) | PP_        |            |                                  |

**[⬆ Back to Top](#table-of-contents)**

<a name="2"></a>
<a name="structure"></a>
## 2. Content Directory Structure

Importanti tanto quanto i nomi degli asset, lo stile della directory di un progetto dovrebbe essere legge. Convenzioni sulla nominazione degli asset e struttura content directory structure vanno mano a mano, e la violazione di anche sola una di esse crea caos evitabile.

Esistono vari modi per organizzare il content di un progetto UE4. In questo stile useremo una struttura che si affida maggiormente al filtering e all'abilità di ricerca del Content Browser per aiutare chiunque lavori con asset a trovare asset di un tipo specifico al posto di un'altra common structure che raggruppa asset types in cartelle.

> Se stai usando il prefisso [naming convention](#1.2) qua sopra indicato, usare cartelle per contenere asset di tipologia simile quali `Meshes`, `Textures`, e `Materials` é una pratica ridondante perchè gli asset types sono già organizzati per prefisso e inoltre filtrati nel content browser.

<a name="2e1"><a>
### 2e1 Example Project Content Structure
<pre>
|-- Content
    |-- <a href="#2.2">GenericShooter</a>
        |-- Art
        |   |-- Industrial
        |   |   |-- Ambient
        |   |   |-- Machinery
        |   |   |-- Pipes
        |   |-- Nature
        |   |   |-- Ambient
        |   |   |-- Foliage
        |   |   |-- Rocks
        |   |   |-- Trees
        |   |-- Office
        |-- Characters
        |   |-- Bob
        |   |-- Common
        |   |   |-- <a href="#2.7">Animations</a>
        |   |   |-- Audio
        |   |-- Jack
        |   |-- Steve
        |   |-- <a href="#2.1.3">Zoe</a>
        |-- <a href="#2.5">Core</a>
        |   |-- Characters
        |   |-- Engine
        |   |-- <a href="#2.1.2">GameModes</a>
        |   |-- Interactables
        |   |-- Pickups
        |   |-- Weapons
        |-- Effects
        |   |-- Electrical
        |   |-- Fire
        |   |-- Weather
        |-- <a href="#2.4">Maps</a>
        |   |-- Campaign1
        |   |-- Campaign2
        |-- <a href="#2.8">MaterialLibrary</a>
        |   |-- Debug
        |   |-- Metal
        |   |-- Paint
        |   |-- Utility
        |   |-- Weathering
        |-- Placeables
        |   |-- Pickups
        |-- Weapons
            |-- Common
            |-- Pistols
            |   |-- DesertEagle
            |   |-- RocketPistol
            |-- Rifles
</pre>

I motivi per cui usare questa struttura sono elencati nelle seguenti sottosezioni.

<a name="2.1"></a>
<a name="structure-folder-names"><a>
### 2.1 Folder Names

Queste sono regole comuni per nominare ogni cartella nella content structure.

<a name="2.1.1"></a>
#### 2.1.1 Usa sempre PascalCase[<sup>*</sup>](#terms-cases)

PascalCase significa iniziare un nome con la prima lettera in maiuscolo, il rimanente della parola in minuscolo e poi ogni parola che segue al posto di essere staccata con lo spazio, si attacca alla prima maiuscolizzando la sua prima lettera . Per esempio, `DesertEagle`, `RocketPistol`, e `ASeriesOfWords`.

Leggi anche [Cases](#terms-cases).

<a name="2.1.2"></a>
#### 2.1.2 Non usare mai la barra spaziatrice

Rafforzando il concetto espresso in [2.1.1](#2.1.1), non usare mai spazi. Essi possono creare vari problemi usando engineering tools e batch processes portandoli a fallire. Idealmente, il root del tuo progetto non ha spazi e si trova in `D:\Project` al posto di `C:\Users\My Name\My Documents\Unreal Projects`.

<a name="2.1.3"></a>
#### 2.1.3 Non usare mai caratteri Unicode e altri symboli

Se uno dei tuoi personaggi del gioco si chiama 'Zoë', il nome della sua cartella dovrebbe essee `Zoe`. Caratteri Unicode possono essere peggio dello [Spaces](#2.1.2) per engineering tool e alcune parti di UE4 non supportano caratteri Unicode nemmeno nei path.

Riguardo ciò, se i tuo progetto ha [unexplained issues](https://answers.unrealengine.com/questions/101207/undefined.html) e il tuo user name del tuo computer ha un carattere Unicode (i.e. your name is `Zoë`), ogni progetto che si trova nella cartella `My Documents` avrà sempre questo problema. Spesso basta semplicemente spostare il tuo progetto in un path come `D:\Project` per risolvere questo problemi misteriosi.

Usare altri caratteri ad eccezione di `a-z`, `A-Z`, e `0-9` come `@`, `-`, `_`, `,`, `*`, e `#` può portare a creare problemi difficili da tracciare in altre piattaforme, source control, and weaker engineering tools.

<a name="2.2"></a>
<a name="structure-top-level"><a>
### 2.2 Usa una cartella Top Level per assets Project Specific

Tutti gli asset di un progetto dovrebbero stare in una cartella chiamata col nome del progetto. Per esempio, se il tuo progetto si chiama 'Generic Shooter', _tutti_ i suoi contenuti dovrebbero stare in `Content/GenericShooter`.

> La cartella `Developers` non  per asset che il tuo progetto usa per funzionare e quindi non sono project specific. Vedi anche [Developer Folders](#2.3) per ulteriori dettagli.

Ci sono più motivi per questo approccioThere are multiple reasons for this approach.

<a name="2.2.1"></a>
#### 2.2.1 No assets per uso globale

Spesso nei manuali di stile di codice viene insegnato che non bisogna sporcare il global namespace e pure questa quida segue questo stesso principio. Quando agli asset viene permesso di esistere fuori dalla cartella del progetto, diventa spesso più difficile far rispettare un layout con una struttura ben precisa poichè gli asset non presenti in una cartella incoraggiano il comportamento errato di non aver da organizzare asset.

Ogni asset dovrebbe avere un suo scopo, o non appartiene al progetto. Se un asset è un test sperimentale e non dovrebbe essere usato dal progetto dovrebbe essere messo in una cartella [`Developer`](#2.3).

<a name="2.2.2"></a>
#### 2.2.2 Riduci i conflitti delle Migration

Quando si lavora a più progetti contemporaneamente é normale per un team copiare asset da un proggetto all'altro se hanno sviluppato quancosa di utile per entrambi i progetti. Quando questo succede, la maniera più facile per fare la copia é usare la funzione Migrate del Content Browser che copierà non solo l'asset selezionato ma tutte le sue dependencies.

Sono proprio queste dependencies che potrebbero dare rogne. Se gli asset di due progetti non hanno una top level folder e inoltre hanno asset con nomi simili o già precedentemente migrati, una nuova migrazione ha la probabile conseguenza di cancellare qualsiasi modifica degli asset già esistenti.

È per questo motivo per cui lo staff del Marketplace della Epic fa rispettare la stessa polici per gli asset pubblicati.

Dopo una migrazione, il safe merging degli asset può essere fatto usando lo strumento 'Replace References' nel content browser col beneficio della maggior chiarezza degli asset non appartenenti alla cartella top level del progetto sono visibilmente in pending per il merge. Una volta che gli asset hanno subito il merge e sono stati completamente migrati, non ci dovrebbe essere un'altra cartella top level nel tuo Content Tree. Questo metodo garantisce al _100%_ di rendere ogni migrazione assolutamente sicura.

<a name="2.2.2e1"></a>
##### 2.2.2e1 Master Material Example

Per esempio, ipotizziamo che hai creato un master material in un progetto e vorresti usarlo in un altro progetto quindi sposto quell'asset. Se questo aset non é in una cartella top level, potrebbe avere un nome come `Content/MaterialLibrary/M_Master`. Se il progetto ricevente non ha un master materialm dovrebbe funzionare tutto senza problemi.

Nel mentre che il lavoro procede in uno o entrambi i progetti, i loro rispettivi master material possono cambiare per essere aggiustati per i loro progetti specifici a causa del progresso normale di sviluppo.

Il problema sorge quando, per esempio, un artista per un progetto crea un buon set generico e modilare di static meshes e qualcuno vuole includere quel set di static meshes nel secondo progetto. Se l'artista che ha creato l'asset ha usato material instances basate su `Content/MaterialLibrary/M_Master` come gli é stato imposto, quando una migrazione viene fatta c'é una forte chanse di conflitti per gli asset `Content/MaterialLibrary/M_Master` già presenti.

Questo problema può essere difficile da predire e a cui dare la colpa. La persona che ha migrato le static meshes può non essere la stessa persona che è familiare con lo sviluppo del master material di entrambi i progetti, e potrebbero nemmeno essere a conoscenza che le static meshes in questione si appoggiano a material instances che poi si appoggiano al master material. Il Migrate tool richiede che tutta la catena di dependencies funzioni e quindi sarà forzata a acchiappare  `Content/MaterialLibrary/M_Master` quando copia questi asset allaltro progetto e sovrascriverà gli asset già esistenti.


È a questo punto che se i master material per entrambi i progetti sono incompatibili in _qualsiasi maniera_, rischi di rompere l'intera material librari di un progetto e ogni dependencies che sono ormai già state migrate, semplicemente perchè gli asset non erano piazzati in una cartella top level. La semplice migrazione di static meshes ora diventa un incubo.

<a name="2.2.3"></a>
#### 2.2.3 Samples, Templates, and Marketplace Content Are Risk-Free


Una aggiunta a [2.2.2](#2.2.2), se un membro del team decide di aggiungere sample content, template files, o assets che hanno comprato dal  marketplace, è garantito, sino a quando la cartella top-level del tuo progetto è nominata in maniera unica, che questi nuovi asset non creeranno interferenze col tuo progetto.

Non puoi fidarti che il contenuto del marketplace sia perfettamente conforme alla [top level folder rule](#2.2).  Esistono tanti asset che pongono la maggior parte del loro contenuto in una cartella top level ma hanno possibilità di contenere sample content della Epic modificato e/o level files che inquinano la cartella globale `Content`.

Quando When adhering to [2.2](#2.2), il peggior conflitto del marketplace che puoi avere è se due assets del marketplace hanno entrambi lo stesso Epic sample content. Se tutti i tuoi asset sono in una cartella specifica del progetto, includendo pure il sample content che puoi aver messo nella tua cartella il tuo progetto non si romperà mai.

<a name="2.2.4"></a>
#### 2.2.4 DLC, Sub-Projects, and Patches Are Easily Maintained

Se il tuo progetto prevede di rilasciare DLC o ha tante sottocartelle associate con esso che possono essere migrate via o semplicemente non cooked in una build, gli asset che si allacciano a questo progetto dovrebbero avere la loro cartella top level. Questo rende cooking DLC un atto separato dal progetto principale molto più facile. Sub-projects possono inoltre essere migrati dentro e fuori col minimo sforzo. Se hai bisogno di cambiare un materiale di un asset o aggiungere un asset override behaviour molto specifico in una patch, puoi facilmente applicare questi cambiamenti in una cartella patch e lavorare in sicurezza senza la chance di rompere il progetto core.

<a name="2.3"></a>
<a name="structure-developers"></a>
### 2.3 Use Developers Folder For Local Testing

Durante lo sviluppo di un progetto, è molto comune per membri del team avere una sorta di 'sandbox' dove possono sperimentare liberamente senza mettere a rischio il core project. Siccome questo lavoro può essere in corso, questi membri del team sarebbe meglio se mettessero i loro asset in un project's source control server. Non tutti i team hanno bisogno delle cartelle Developer, ma chi le usa spesso incorrono nel problema di avere assets.

È molto facile per un membro del team usare asset che non sono pronti all'uso, che causerà problemi quando questi saranno rimossi. Per eempio, un artista potrebbe iterating in un set modulare di static meshes e lavorarci sopra impostando il loro sizing e grid snapping in maniera corretta. Se un world builder vede questi asset nella cartella principale del progetto, potrebbero usarli in un livello senza sapere che questi potrebbero essere sottoposti a cambi incredibili e/o rimozione. Ciò causa quantità immense di re-working per tutti i membri del team da risolvere.

Se questi asset modulari fossero piazzati nella cartella Developer, il world builder non avrebbe mai scuse per usarli e questo problema non sarebbe mai successo. Il Content Browser ha una specifica View Options che nascondere le cartelle Developer (sono nascoste di default) rendendo impossibile l'uso accidentale di asset di Developer in circostanze normali.

Una volta che questi asset sono pronti all'uso, una artista semplicemente deve spostare gli asset nella cartella specifica del progetto e fixare i redirectors. Fare ciò è 'promuovere' gli asset da sperimentali a produzione.

<a name="2.4"></a>
<a name="structure-maps"></a>
### 2.4 All Map[<sup>*</sup>](#terms-level-map) Files appartengono a una cartella chiamata Maps

Map files sono incredibilmente speciali ed è normale per ogni progetto che esso abbia il suo sistema di denominazione proprio, specialmente se si lavora con sottolivelli o streaming levels. A prescindere da quale sistema di organizzazione map è usato per il progetto specifico, tutti i levels dovrebbero stare in `/Content/Project/Maps`.

Essere in grado di dire a qualcuno di aprire una map specifica senza dover spiegare dove si trova è un ottimo modo per risparmiare tempo e miglioramento della 'quality of life'. È comune per i levels stare in sottocartelle di `Maps`, come per esempio `Maps/Campaign1/` o `Maps/Arenas`, ma la cosa più importante è che tutte stiano all'interno di `/Content/Project/Maps`.

Questo inoltre semplifica il lavoro di cooking per li ingegnieri. Wrangling levels for a build process può essere estremamente frustrante se hanno da scavare  dig through arbitrary cartelle for them. Se le maps di un team sono tutte in un posto, è molto pù difficile dimenticarsi di far un cook di una map in una build. Semplifica inoltre script di lighting build e processi di QA.

<a name="2.5"></a>
<a name="structure-core"></a>
### 2.5 Use A `Core` Folder For Critical Blueprints And Other Assets

Use `/Content/Project/Core` folder for assets that are absolutely fundamental to a project's workings. For example, base `GameMode`, `Character`, `PlayerController`, `GameState`, `PlayerState`, and related Blueprints should live here.

This creates a very clear "don't touch these" message for other team members. Non-engineers should have very little reason to enter the `Core` folder. Following good code structure style, designers should be making their gameplay tweaks in child classes that expose functionality. World builders should be using prefab Blueprints in designated folders instead of potentially abusing base classes.

For example, if your project requires pickups that can be placed in a level, there should exist a base Pickup class in `Core/Pickups` that defines base behavior for a pickup. Specific pickups such as a Health or Ammo should exist in a folder such as `/Content/Project/Placeables/Pickups/`. Game designers can define and tweak pickups in this folder however they please, but they should not touch `Core/Pickups` as they may unintentionally break pickups project-wide.

<a name="2.6"></a>
<a name="structure-assettypes"></a>
### 2.6 Do Not Create Folders Called `Assets` or `AssetTypes`

<a name="2.6.1"></a>
#### 2.6.1 Creating a folder named `Assets` is redundant

Tutti gli asset sono asset.

<a name="2.6.2"></a>
#### 2.6.2 Creating a folder named `Meshes`, `Textures`, or `Materials` is redundant

Tutti i nomi degli assset sono decisi tenendo sempre conto del loro asset type. Queste cartelle offrono solo informazioni ridondanti e l'uso di esse può essere facilmente rimpiazzato dal robuto e facile all'uso filter system dato a disposizione dal Content Browsers.

Vuoi vedere solo le static mesh in `Environment/Rocks/`? Semplicemente attiva il filtro Shatic Mesh. Se tutti gli asset sono nominati correttamente, allora saranno organizzati in ordine alfabetico a prescindere dal prefisso. Vuoi vedere sia le static meshes e le skeletal meshes? Semplicemente attiva entrambi i filtri. Questo elimina la necessità di potenzialmente aver da fare `Control-Click` selezionare due cartelle nella tree view del Content Browser.

> Questo discorso si estende anche al full path name di un asset per alcuni benefici. Il prefisso `S_` per una static mesh è composto da soli due caratteri, invece `Meshes/` sono ben sette caratteri.

Non fare questo inoltre previene l'inevitabilità di qualcuno a mettere una static mesh o una texture nella cartella `Materials`.

<a name="2.7"></a>
<a name="structure-large-sets"></a>
### 2.7 Very Large Asset Sets Get Their Own Folder Layout

Questa può essre intesa come una pseudo-eccezione alla regola [2.6](#2.6).

Esisono certi tipi di asset che hanno un numero alto di relativi file dove ogni asset ha un suo scopo unico. I due più comuni sono gli asset Animation e Audio. Se ti trovi con 15+ di questi asset che appartengono l'un l'altro, questi dovrebbero stare assieme.

Per esempio, animazioni che sono condivise tra molteplici personaggi dovrebbero stare in `Characters/Common/Animations` e possono avere sottocartelle come `Locomotion` o `Cinematic`.

> Ciò non si applica agli asset come textures e materials. È normale per una cartella `Rocks` avere un numero importante di texture se ci sono tante rocce, tuttavia queste texture sono generalmente solo relazionate a un paio di specifiche rocce e dovrebbero essere nominate in maniera opportuna. Pure se queste texture sono parte di una [Material Library](#2.8).

<a name="2.8"></a>
<a name="structure-material-library"></a>
### 2.8 `MaterialLibrary`

Se il tuo progetto fa uso di master materials, layered materials, o ogni forma di reusable materials o textures che non appartengono a nessun any subset di assets, questi asset devonon essere piazzati in `Content/Project/MaterialLibrary`.

In questa maniera tutti i materials 'global' hanno un posto dove stare e sono facilmente piazzati.

> Ciò rende inoltre incredibilmente facile rafforzare una policy di 'use material instances only' all'interno di un progetto. Se tutti gli artisti e asset dovrebbero usare material instances, allora i soli regular material assets che dovrebbero esistere esistono solo dentro questa cartella. Puoi verificare facilmente questo cercando per base materials in ogni cartella che non è `MaterialLibrary`.

La `MaterialLibrary` non deve per forza contenere solo materials. Shared utility textures, material functions, e altre cose di simile natura dovrebbero essere conservate qui e inoltre dentro cartelle che indicano il loro scopo. Per esempio, generic noise textures dovrebbero essere piazzate in `MaterialLibrary/Utility`.

Qualsiasi testing o debug materials dovrebbe stare all'interno dei confini di `MaterialLibrary/Debug`. Ciò permette debug materials di essere facilmente stripped da un progetto prima dello shipping e rende in maniera incredibilmente apparente se dei production assets li lstanno usando are using them se reference errors sono mostrati.

<a name="2.9"></a>
<a name="structure-no-empty-folders"></a>
### 2.9 No Empty Folders

In pratica, non dovrebbero esserci mai cartelle vuote. Creano disordine nel Content Browser.

Se noti che il content Browser ha una cartella vuota che non puoi cancellare, dovresti provare le seguenti soluzioni:
1. Sii sicuro che stai usando source control.
1. Immediatamente avvia Fix Up Redirectors nel tuo progetto.
1. Arriva alla cartella on-disk e cancella gli asset presenti dentro.
1. Chiudi l'editor.
1. Assicurati che il tuo source control state sia in sync (i.e. se usi Perforce, avvia un Reconcile Offline Work nella tua content directory)
1. Apri l'editor. Conferma che tutto funzioni come ci si aspetti. Se non, fai revert, trova l'errore e riprova.
1. Assicurati che la cartella sia sparita.
1. Fai Submit changes al source control.

**[⬆ Back to Top](#table-of-contents)**


<a name="3"></a>
<a name="bp"></a>
## 3. Blueprints

Questa sezione si concentra sulle Blueprint classes e i loro meccanismi interni. Quando possibile,il manuale di stile rispetta il [Epic's Coding Standard](https://docs.unrealengine.com/latest/INT/Programming/Development/CodingStandard).

Ricorda: Blueprinting badly bears blunders, beware! (Phrase by [KorkuVeren](http://github.com/KorkuVeren))

<a name="3.1"></a>
<a name="bp-compiling"></a>
### 3.1 Compiling

Tutti i blueprint dovrebbero compilare senza avvisi e/o errori. Dovresti fixare warnings e errors immediatamente poichè possono molto velocemente creare comportamenti inaspettati.

*Non* mandare in submit blueprint rotti al source control. Se devi conservarli nel source control, considera invece mandarli in shelve.

Blueprint rotti possono causare problemi che si manifestano in altre maniere, come broken references, unexpected behavior, cooking failures, e frequenti recompilation non necessarie. Un blueprint rotto ha la capacità di rompere tutto il tuo gioco.

<a name="3.2"></a>
<a name="bp-vars"></a>
### 3.2 Variables

Le parole `variable` e `property` possono entrambe essere usate per indicare lo stesso concetto.

<a name="3.2.1"></a>
<a name="bp-var-naming"></a>
#### 3.2.1 Naming

<a name="3.2.1.1"></a>
<a name="bp-var-naming-nouns"></a>
##### 3.2.1.1 Nouns

Tutti i nomi delle non-boolean variable devono essere sostantivi chiari, non ambigui, e descrittivi.

<a name="3.2.1.2"></a>
<a name="bp-var-naming-case"></a>
##### 3.2.1.2 PascalCase

Tutte le non-boolean variables dovrebbero essere nella forma [PascalCase](#terms-cases).

<a name="3.2.1.2e"></a>
###### 3.2.1.2e Esempi

* `Score`
* `Kills`
* `TargetPlayer`
* `Range`
* `CrosshairColor`
* `AbilityID`

<a name="3.2.1.3"></a>
<a name="bp-var-bool-prefix"></a>
##### 3.2.1.3 Boolean `b` Prefix

Tutti i booleans dovrebbero essere nominati in PascalCase ma prefissati con una `b` minuscola.

Esempi: Usa `bDead` e `bEvil`, **non** `Dead` e `Evil`.

Gli editor di blueprint per UE4 sanno che non devono far vedere la `b` della variable nelle esposizioni visive user-friendly.

<a name="3.2.1.4"></a>
<a name="bp-var-bool-names"></a>
##### 3.2.1.4 Boolean Names

<a name="3.2.1.4.1"></a>
###### 3.2.1.4.1 General And Independent State Information

Tutti i boolean dovrebbero essere nominati come aggettivi descrittivi quando possibile se rappresentano informazioni generiche. Non includere parole che impostano la variable come una domanda, come per esempio `Is`. Quello è riservato alle functions.

Esempio: usa `bDead` e `bHostile` **non** `bIsDead` e `bIsHostile`.

Cerca di non usare verbi come `bRunning`. Verbs tend to lead to complex states.

<a name="3.2.1.4.2"></a>
###### 3.2.1.4.2 Complex States

Non usare booleans per rappresentare complex e/o dependent states. Ciò rende state adding e removing troppo complesso e non più facilmente leggibile. Piuttosto usa l'enumeration.

Esempio: quando definisci un'arma, **non** usare `bReloading` e `bEquipping` se un'arma non essere in entrambi gli stati di reloading e equipping contemporeaneamente. Piuttosto definisci un enumeration nominato `EWeaponState` e usa una variable con questo tipo chiamata `WeaponState`. Fare ciò facilita aggiungere nuovi states alle armi.

Esempio: **non** usare `bRunning` se hai bisogno pure di `bWalking` o `bSprinting`. Ciò dovrebbe essere definito da un enumeration con state names chiari e definiti.

<a name="3.2.1.5"></a>
<a name="bp-vars-naming-context"></a>
##### 3.2.1.5 Considered Context

Tutti i variable names non devono essere ridondanti con il loro contesto poichè tutte le  variable references in Blueprint hanno sempre contesto.

<a name="3.2.1.5e"></a>
###### 3.2.1.5e Esempi

Considera un Blueprint chiamato `BP_PlayerCharacter`.

**Cattiva pratica**

* `PlayerScore`
* `PlayerKills`
* `MyTargetPlayer`
* `MyCharacterName`
* `CharacterSkills`
* `ChosenCharacterSkin`

Tutte queste variables sono nominate in maniera ridondante. È implicato che la variable è rappresentativa del `BP_PlayerCharacter` a cui appartiene perchè è `BP_PlayerCharacter` che definisce queste variables.

**Buona pratica**

* `Score`
* `Kills`
* `TargetPlayer`
* `Name`
* `Skills`
* `Skin`

<a name="3.2.1.6"></a>
<a name="bp-vars-naming-atomic"></a>
##### 3.2.1.6 Do _Not_ Include Atomic Type Names

Atomic or primitive variables sono variables che rappreentano data nella loro forma più semplice, come booleans, integers, floats, e enumerations.

Strings e vectors sono considerati atomic in termini di stile quando si lavora con i Blueprints, tuttavia tecnicamente non sono atomici.

> Mentre i vectors consistono in tre floats, vectors sono spesso in grado di essere manipolati come un insieme, stesso disorso per i rotators.

> _Non_ considerare Text variables come atomic, stanno segretamente nascondendo localization functionality. L'atomic type di una stringa di caratteri è `String`, non `Text`.

Atomic variables non dovrebbero avere il loro type name nel loro nome.

Esempio; usa `Score`, `Kills`, e `Description` **non** `ScoreFloat`, `FloatKills`, `DescriptionString`.

L'unica eccezione a questa regola è quando una variable rappresenta 'un numero di' qualcosa da essere contato _e_ quando usando un nome senza un  variable type non è facile da leggere.

Esempio: un generatore di recizione ha bisogno di generare un tot X di paletti, chiamati in inglese posts. Conserva X in `NumPosts` o `PostsCount` invece di `Posts` poichè `Posts` potrebbe essre interpretato come un Array di un variable type dei `Post`.

<a name="3.2.1.7"></a>
<a name="bp-vars-naming-complex"></a>
##### 3.2.1.7 Do Include Non-Atomic Type Names

Non-atomic o complex variables sono variables che rappresentano data come collezione di atomic variables. Structs, Classes, Interfaces, e primitives con hidden behavior quali `Text` e `Name` stanno tutti dentro questa regola.

> Sebbene un Array di un atomic variable type è una lista di variables, gli Arrays non cambiano la 'atomicness' del variable type.

Queste variables dovrebbero includere il loro type name sempre tenendo in considerazione il loro contesto.

Se una class possiede una instance di una complex variable, i.e. se un `BP_PlayerCharacter` possiede un `BP_Hat`, quest'ultima dovrebbe essere classificata come la variable type senza modifiche sul nome.

Esempio: usa `Hat`, `Flag`, e `Ability` **non** `MyHat`, `MyFlag`, e `PlayerAbility`.

Se una class non possiede la value che la complex variable rappresenta, dovresti usare un sostantivo you should use a noun seguente la variable type.

Esempio: se un `BP_Turret` ha l'abilità di targettare un `BP_PlayerCharacter`, dovrebbe conservare il suo target come `TargetPlayer` poichè nel contesto di `BP_Turret` dovrebbe essere chiaro che è una reference a un altro complex variable type che non possiede.


<a name="3.2.1.8"></a>
<a name="bp-vars-naming-arrays"></a>
##### 3.2.1.8 Arrays

Arrays seguono le stesse regole di nominazione qua sopra descritte, ma dovrebbero essere nominate con sostantivi plurali.

Esempio: usa `Targets`, `Hats`, e `EnemyPlayers`, **non** `TargetList`, `HatArray`, `EnemyPlayerArray`.


<a name="3.2.2"></a>
<a name="bp-vars-editable"></a>
#### 3.2.2 Editable Variables

Tutte le variables di cui è sicuro cambiarne la value in modo da configurare il comportamento di un blueprint dovrebbero essere segnate come `Editable`.

Invece, tutte le variables che non sono sicure da cambiare o non dovrebbero essere esposte ai designer _non_ devono essere segnate come editable, tranne per quei motivi di engineering dove allora la variable deve essere segnata come `Expose On Spawn`.

Non segnare arbitrariamente qualsiasi variables come `Editable`.

<a name="3.2.2.1"></a>
<a name="bp-vars-editable-tooltips"></a>
##### 3.2.2.1 Tooltips

Tutte le variables `Editable`, includendo pure quelle segnate come editable giusto per rientrare nella categoria `Expose On Spawn`, dovrebbero avere una descrizione nei loro campi `Tooltip` che spiegano come cambiare questa value cambia il behavior del blueprint.

<a name="3.2.2.2"></a>
<a name="bp-vars-editable-ranges"></a>
##### 3.2.2.2 Slider And Value Ranges

Tutte le variables `Editable`dovrebbero fare uso dello slide e dei value ranges se mai ci fosse una value a cui la variable _non_ dovrebbe essere settata.

Esempio: un blueprint che genera paletti, in inglese posts, per una recinzione potrebbe avere una editable variable chiamata `PostsCount` e una value di -1 non avrebbe alcun senso. Usa i range fields per impostare 0 come valore minimo.

Se una editable variable è usata in un Construction Script, dovrebbe avere uno Slider Range definito e limitato, in modo che nessuno possa per errore dargli una value troppo alta e far crashare l'editor di conseguenzade.

Il Value Range ha bisogno di essere definito solo se i limiti della value sono conosciuti. Mentre uno Slider Range previene l'input per errore di numeri grossi, un undefined Value Range permette all'utente di specificare la value fuori dallo Slider Range che può essere considerato 'pericoloso' ma tuttavia valido.

<a name="3.2.3"></a>
<a name="bp-vars-categories"></a>
#### 3.2.3 Categories

Se una class ha solo un poccolo numero di variables, le categories non sono richieste.

Se una class ha un numero modesto di variables (5-10), tutte le variables `Editable` dovrebbero avere assegnata non-default. Una category comune è `Config`.

Se una class ha un numero grosso di variables, tutte le variables `Editable` dovrebbero essere categorizzate in sub-categories usando la category `Config` come base category. Non-editable variables dovrebbero essere categorizzate in descriptive categories descrivendo il loro utilizzo.

> Puoi definire sub-categories usando il pipe character `|`, i.e. `Config | Animations`.

Esempio: un weapon class set di variables potrebbe essere organizzato così:

    |-- Config
    |    |-- Animations
    |    |-- Effects
    |    |-- Audio
    |    |-- Recoil
    |    |-- Timings
    |-- Animations
    |-- State
    |-- Visuals

<a name="3.2.4"></a>
<a name="bp-vars-access"></a>
#### 3.2.4 Variable Access Level

In C++, variables hanno il concetto di access level. Public significa ogni codice fuori dalla classe può accedere alla variable. Protected significa che solo la class e ogni child classes può accedere a questa variable. Private significa che solo questa class e nessuna delle child classes può accedere a questa variable.

I Blueprints ora come ora non hanno un defined concept di protected access.

Tratta `Editable` variables come public variables. Tratta non-editable variables come protected variables.

<a name="3.2.4.1"></a>
<a name="bp-vars-access-private"></a>
##### 3.2.4.1 Private Variables

A meno che non si sappia che una variable dovrebbe essere accessibile solo all'interno della class in cui è definita e mai una child class, non segnare queste variables come private. Sino a quando le variables sono in grado di essere segnate come `protected`, risparmia il private per quando sai con sicurezza che vuoi restringere il child class usage.

<a name="3.2.5"></a>
<a name="bp-vars-advanced"></a>
#### 3.2.5 Advanced Display

Se una variable dovrebbe essere editable ma spesso untouched, marchiala come `Advanced Display`. Questo rende la variable nascosta a meno che la frecca advanced diplay sia clickata.

Per trovare l'opzione `Advanced Display` , è mostrata come una advanced displayed variable nella lista variable details.

<a name="3.2.6"></a>
<a name="bp-vars-transient"></a>
#### 3.2.6 Transient Variables

Le Transient variables sono variables che non hanno bisogno che la loro value sia salvata e caricata e hanno una value iniziale pari a zero o null. Ciò è utile per references a altri objects e actors il cui loro valore non è saputo sino al run-time. Ciò previene che l'editor salvi una reference verso essa, e velocizza salvare e caricare dalla blueprint class.

A causa di questo, tutte le transient variables dovrebbero sempre essere initialized come zero o null. Non fare questo creerebbe errori difficili da risolvere.

<a name="3.2.7"></a>
<a name="bp-vars-config"></a>
#### 3.2.8 Config Variables

Non usare la flag `Config Variable`. Questa rende difficile ai designer controllare il comportamento del blueprint. Le Config variables dovrebbero essere usate solo in C++ per variables che cambiate raramente. Pensa ad esse come se fossero `Advanced Advanced Display` variables.

<a name="3.3"></a>
<a name="bp-functions"></a>
### 3.3 Functions, Events, and Event Dispatchers

Questa sezione descrive come dovresti author functions, events, e event dispatchers. Tutto ciò che si applica alle functions si applica pure agli eventi, tranne ciò di cui viene fatta nota.

<a name="3.3.1"></a>
<a name="bp-funcs-naming"></a>
#### 3.3.1 Function Naming

La nominazione di functions, events, e event dispatchers è di importanza critica. Basandosi solamente sul nome, certe assunzioni possono essere fatte sulle function. Per esempio:

* È una pure function?
* Sta fetching state information?
* È un handler?
* È un RPC?
* Quale è il suo scopo?

Queste domande e altre possono essere riposte quando le funziono sono nominate in maniera appropriata.

<a name="3.3.1.1"></a>
<a name="bp-funcs-naming-verbs"></a>
#### 3.3.1.1 All Functions Should Be Verbs

Tutte le functions e events fanno qualche forma di azione, che sia prendere info, calcolare data, o far esplodere qualcosa. Di conseguenza, tutte le functions dovrebbero iniziare con verbi. Dovrebbero essere coniugate nel presente quando possibile. Dovrebbero avere anche del contesto riguardante cosa fanno.

`OnRep` functions, event handlers, e event dispatchers sono una eccezione a questa regola.

Buoni esempi:

* `Fire` - Buon esempio se è in un Character / Weapon class, perchè ha contesto. Cattivo esempio se è in un Barrel / Grass / qualsiasi class poco chiara.
* `Jump` - Buon esempio se è in un Character class, altrimenti ha bisogno di contesto.
* `Explode`
* `ReceiveMessage`
* `SortPlayerArray`
* `GetArmOffset`
* `GetCoordinates`
* `UpdateTransforms`
* `EnableBigHeadMode`
* `IsEnemy` - ["Is" è un verbo.](http://writingexplained.org/is-is-a-verb)

Cattivi esempi:

* `Dead` - È morto? Morirà?
* `Rock`
* `ProcessData` - Ambiguo, queste parole non significano niente.
* `PlayerState` - I sostantivi sono ambigui.
* `Color` - Verbo senza contesto, sostantivo ambiguo.

<a name="3.3.1.2"></a>
<a name="bp-funcs-naming-onrep"></a>
#### 3.3.1.2 Property RepNotify Functions Always `OnRep_Variable`

Tutte le functions for replicated con notification variables dovrebbero avere la form `OnRep_Variable`. Ciò è forzato dal Blueprint editor. Se stai scrivendo una function in C++ `OnRep` tuttavia, dovrebbe seguire questa convenzione quando la esponi ai Blueprints.

<a name="3.3.1.3"></a>
<a name="bp-funcs-naming-bool"></a>
#### 3.3.1.3 Info Functions Returning Bool Should Ask Questions

Quando scrivi una function che non cambia lo state di o modifica qualsasi object e è puramente per ottenere information, state, o computing a yes/no value, dovrebbe fare una domanda. Questo dovrebbe inoltre seguire la [the verb rule](#bp-funcs-naming-verbs).

Questo è estremamente importante perchè se una domanda non viene fatta, può essere dato per scontato che la function faccia una action e stia riferendo se quell'action ha avuto successo.

Buoni esempi:

* `IsDead`
* `IsOnFire`
* `IsAlive`
* `IsSpeaking`
* `IsHavingAnExistentialCrisis`
* `IsVisible`
* `HasWeapon` - ["Has" è un verbo.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)
* `WasCharging` - ["Was" è il past-tense di "be".](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html) Usa "was" quando ti riferisci a 'previous frame' o 'previous state'.
* `CanReload` - ["Can" è un verbo.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)

Cattivi esempi:

* `Fire` - È a fuoco? Sparerà? Spara?
* `OnFire` - Può essere confuso con un event dispatcher per sparare.
* `Dead` - È morto? Morirà?
* `Visibility` - È visibile? Imposta visibilità? È una descrizione di condizioni di volo?

<a name="3.3.1.4"></a>
<a name="bp-funcs-naming-eventhandlers"></a>
#### 3.3.1.4 Event Handlers e Dispatchers Should Start With `On`

Qualsiasi function that handles un event o dispatches un event dovrebbe iniziare con `On` e continuare [the verb rule](#bp-funcs-naming-verbs). Il verbo si può sèpstare alla fine se, in caso di coniugazione in past-tense, rende meglio.

[Collocations](http://dictionary.cambridge.org/us/grammar/british-grammar/about-words-clauses-and-sentences/collocation) della parola `On` sono esenti dal seguire la regola del verbo.

`Handle` non è permesso. È 'Unreal' usare `On` al posto di `Handle`, mentre altri frameworks possono preferire usare `Handle` al posto di `On`.

Esempi corretti:

* `OnDeath` - Common collocation in games
* `OnPickup`
* `OnReceiveMessage`
* `OnMessageRecieved`
* `OnTargetChanged`
* `OnClick`
* `OnLeave`

Cattivi esempi:

* `OnData`
* `OnTarget`
* `HandleMessage`
* `HandleDeath`

<a name="3.3.1.5"></a>
<a name="bp-funcs-naming-rpcs"></a>
#### 3.3.1.5 Remote Procedure Calls Should Be Prefixed With Target

Ogni volta che una RPC viene creata, dovrebbe essere prefissata con `Server`, `Client`, o `Multicast`. Nessuna eccezione.

Dopo il prefisso, segui tutte le altre regole riguardandi la nominazione delle function.

Esempi corretti:

* `ServerFireWeapon`
* `ClientNotifyDeath`
* `MulticastSpawnTracerEffect`

Cattivi esempi:

* `FireWeapon` - Does not indicate its an RPC of some kind.
* `ServerClientBroadcast` - Confusing.
* `AllNotifyDeath` - Use `Multicast`, never `All`.
* `ClientWeapon` - No verb, ambiguous.


<a name="3.3.2"></a>
<a name="bp-funcs-return"></a>
#### 3.3.2 All Functions Must Have Return Nodes

All functions must have return nodes, no exceptions.

Return nodes explicitly note that a function has finished its execution. In a world where blueprints can be filled with `Sequence`, `ForLoopWithBreak`, and backwards reroute nodes, explicit execution flow is important for readability, maintenance, and easier debugging.

The Blueprint compiler is able to follow the flow of execution and will warn you if there is a branch of your code with an unhandled return or bad flow if you use return nodes.

In situations like where a programmer may add a pin to a Sequence node or add logic after a for loop completes but the loop iteration might return early, this can often result in an accidental error in code flow. The warnings the Blueprint compiler will alert everyone of these issues immediately.

<a name="3.3.3"></a>
<a name="bp-graphs-funcs-node-limit"></a>
#### 3.3.3 No Function Should Have More Than 50 Nodes

Simply, no function should have more than 50 nodes. Any function this big should be broken down into smaller functions for readability and ease of maintenance.

The following nodes are not counted as they are deemed to not increase function complexity:

* Comment
* Route
* Cast
* Getting a Variable
* Breaking a Struct
* Function Entry
* Self

<a name="3.3.4"></a>
<a name="bp-graphs-funcs-description"></a>
#### 3.3.4 All Public Functions Should Have A Description

This rule applies more to public facing or marketplace blueprints, so that others can more easily navigate and consume your blueprint API.

Simply, any function that has an access specificer of Public should have its description filled out.
#### 3.3.4 All Public Functions Should Have A Description

This rule applies more to public facing or marketplace blueprints, so that others can more easily navigate and consume your blueprint API.

Simply, any function that has an access specificer of Public should have its description filled out.

<a name="3.3.5"></a>
<a name="bp-graphs-funcs-plugin-category"></a>
#### 3.3.5 All Custom Static Plugin `BlueprintCallable` Functions Must Be Categorized By Plugin Name

If your project includes a plugin that defines `static` `BlueprintCallable` functions, they should have their category set to the plugin's name or a subset category of the plugin's name.

For example, `Zed Camera Interface` or `Zed Camera Interface | Image Capturing`.

<a name="3.4"></a>
<a name="bp-graphs"></a>
### 3.4 Blueprint Graphs

This section covers things that apply to all Blueprint graphs.

<a name="3.4.1"></a>
<a name="bp-graphs-spaghetti"></a>
#### 3.4.1 No Spaghetti

Wires should have clear beginnings and ends. You should never have to mentally untangle wires to make sense of a graph. Many of the following sections are dedicated to reducing spaghetti.

<a name="3.4.2"></a>
<a name="bp-graphs-align-wires"></a>
#### 3.4.2 Align Wires Not Nodes

Always align wires, not nodes. You can't always control the size and pin location on a node, but you can always control the location of a node and thus control the wires. Straight wires provide clear linear flow. Wiggly wires wear wits wickedly. You can straighten wires by using the Straighten Connections command with BP nodes selected. Hotkey: Q

Good example: The tops of the nodes are staggered to keep a perfectly straight white exec line.
![Aligned By Wires](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-good.png?raw=true "Aligned By Wires")

Bad Example: The tops of the nodes are aligned creating a wiggly white exec line.
![Bad](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-bad.png?raw=true "Wiggly")

Acceptable Example: Certain nodes might not cooperate no matter how you use the alignment tools. In this situation, try to minimize the wiggle by bringing the node in closer.
![Acceptable](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-acceptable.png?raw=true "Acceptable")

<a name="3.4.3"></a>
<a name="bp-graphs-exec-first-class"></a>
#### 3.4.3 White Exec Lines Are Top Priority

If you ever have to decide between straightening a linear white exec line or straightening data lines of some kind, always straighten the white exec line.

<a name="3.4.4"></a>
<a name="bp-graphs-block-comments"></a>
#### 3.4.4 Graphs Should Be Reasonably Commented

Blocks of nodes should be wrapped in comments that describe their higher-level behavior. While every function should be well named so that each individual node is easily readable and understandable, groups of nodes contributing to a purpose should have their purpose described in a comment block. If a function does not have many blocks of nodes and its clear that the nodes are serving a direct purpose in the function's goal, then they do not need to be commented as the function name and  description should suffice.

<a name="3.4.5"></a>
<a name="bp-graphs-cast-error-handling"></a>
#### 3.4.5 Graphs Should Handle Casting Errors Where Appropriate

If a function or event assumes that a cast always succeeds, it should appropriately report a failure in logic if the cast fails. This lets others know why something that is 'supposed to work' doesn't. A function should also attempt a graceful recover after a failed cast if it's known that the reference being casted could ever fail to be casted.

This does not mean every cast node should have its failure handled. In many cases, especially events regarding things like collisions, it is expected that execution flow terminates on a failed cast quietly.

<a name="3.4.6"></a>
<a name="bp-graphs-dangling-nodes"></a>
#### 3.4.6 Graphs Should Not Have Any Dangling / Loose / Dead Nodes

All nodes in all blueprint graphs must have a purpose. You should not leave dangling blueprint nodes around that have no purpose or are not executed.

**[⬆ Back to Top](#table-of-contents)**


<a name="4"></a>
<a name="Static Meshes"></a>
<a name="s"></a>
## 4. Static Meshes

This section will focus on Static Mesh assets and their internals.

<a name="4.1"></a>
<a name="s-uvs"></a>
### 4.1 Static Mesh UVs

If Linter is reporting bad UVs and you can't seem to track it down, open the resulting `.log` file in your project's `Saved/Logs` folder for exact details as to why it's failing. I am hoping to include these messages in the Lint report in the future.

<a name="4.1.1"></a>
<a name="s-uvs-no-missing"></a>
#### 4.1.1 All Meshes Must Have UVs

Pretty simple. All meshes, regardless how they are to be used, should not be missing UVs.

<a name="4.1.2"></a>
<a name="s-uvs-no-overlapping"></a>
#### 4.1.2 All Meshes Must Not Have Overlapping UVs for Lightmaps

Pretty simple. All meshes, regardless how they are to be used, should have valid non-overlapping UVs.

<a name="4.2"></a>
<a name="s-lods"></a>
### 4.2 LODs Should Be Set Up Correctly

This is a subjective check on a per-project basis, but as a general rule any mesh that can be seen at varying distances should have proper LODs.

<a name="4.3"></a>
<a name="s-modular-snapping"></a>
### 4.3 Modular Socketless Assets Should Snap To The Grid Cleanly

This is a subjective check on a per-asset basis, however any modular socketless assets should snap together cleanly based on the project's grid settings.

It is up to the project whether to snap based on a power of 2 grid or on a base 10 grid. However if you are authoring modular socketless assets for the marketplace, Epic's requirement is that they snap cleanly when the grid is set to 10 units or bigger.

<a name="4.4"></a>
<a name="s-collision"></a>
### 4.4 All Meshes Must Have Collision

Regardless of whether an asset is going to be used for collision in a level, all meshes should have proper collision defined. This helps the engine with things such as bounds calculations, occlusion, and lighting. Collision should also be well-formed to the asset.

<a name="4.5"></a>
<a name="s-scaled"></a>
### 4.5 All Meshes Should Be Scaled Correctly

This is a subjective check on a per-project basis, however all assets should be scaled correctly to their project. Level designers or blueprint authors should not have to tweak the scale of meshes to get them to confirm in the editor. Scaling meshes in the engine should be treated as a scale override, not a scale correction.

**[⬆ Back to Top](#table-of-contents)**


<a name="5"></a>
<a name="Niagara"></a>
<a name="ng"></a>
## 5. Niagara

This section will focus on Niagara assets and their internals.

<a name="5.1"></a>
<a name="ng-rules"></a>
### 5.1 No Spaces, Ever

As mentioned in [00.1 Forbidden Identifiers](#00), spaces and all white space characters are forbidden in identifiers. This is especially true for Niagara systems as it makes working with things significantly harder if not impossible when working with HLSL or other means of scripting within Niagara and trying to reference an identifier.

(Original Contribution by [@dunenkoff](https://github.com/Allar/ue5-style-guide/issues/58))


**[⬆ Back to Top](#table-of-contents)**


<a name="6"></a>
<a name="Levels"></a>
<a name="levels"></a>
## 6. Levels / Maps

[See Terminology Note](#terms-level-map) regarding "levels" vs "maps".

This section will focus on Level assets and their internals.

<a name="6.1"></a>
<a name="levels-no-errors-or-warnings"></a>
### 6.1 No Errors Or Warnings

All levels should load with zero errors or warnings. If a level loads with any errors or warnings, they should be fixed immediately to prevent cascading issues.

You can run a map check on an open level in the editor by using the console command "map check".

Please note: Linter is even more strict on this than the editor is currently, and will catch load errors that the editor will resolve on its own.

<a name="6.2"></a>
<a name="levels-lighting-should-be-built"></a>
### 6.2 Lighting Should Be Built

It is normal during development for levels to occasionally not have lighting built. When doing a test/internal/shipping build or any build that is to be distributed however, lighting should always be built.

<a name="6.3"></a>
<a name="levels-no-visible-z-fighting"></a>
### 6.3 No Player Visible Z Fighting

Levels should not have any [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) in all areas visible to the player.

<a name="6.4"></a>
<a name="levels-mp-rules"></a>
### 6.4 Marketplace Specific Rules

If a project is to be sold on the UE4 Marketplace, it must follow these rules.

<a name="6.4.1"></a>
<a name="levels-mp-rules-overview"></a>
#### 6.4.1 Overview Level

If your project contains assets that should be visualized or demoed, you must have a map within your project that contains the name "Overview".

This overview map, if it is visualizing assets, should be set up according to [Epic's guidelines](http://help.epicgames.com/customer/en/portal/articles/2592186-marketplace-submission-guidelines-preparing-your-assets#Required%20Levels%20and%20Maps).

For example, `InteractionComponent_Overview`.

<a name="6.4.2"></a>
<a name="levels-mp-rules-demo"></a>
#### 6.4.2 Demo Level

If your project contains assets that should be demoed or come with some sort of tutorial, you must have a map within your project that contains the name "Demo". This level should also contain documentation within it in some form that illustrates how to use your project. See Epic's Content Examples project for good examples on how to do this.

If your project is a gameplay mechanic or other form of system as opposed to an art pack, this can be the same as your "Overview" map.

For example, `InteractionComponent_Overview_Demo`, `ExplosionKit_Demo`.

**[⬆ Back to Top](#table-of-contents)**


<a name="7"></a>
<a name="textures"></a>
## 7. Textures

This section will focus on Texture assets and their internals.

<a name="7.1"></a>
<a name="textures-dimensions"></a>
### 7.1 Dimensions Are Powers of 2

All textures, except for UI textures, must have its dimensions in multiples of powers of 2. Textures do not have to be square.

For example, `128x512`, `1024x1024`, `2048x1024`, `1024x2048`, `1x512`.

<a name="7.2"></a>
<a name="textures-density"></a>
### 7.2 Texture Density Should Be Uniform

All textures should be of a size appropriate for their standard use case. Appropriate texture density varies from project to project, but all textures within that project should have a consistent density.

For example, if a project's texture density is 8 pixel per 1 unit, a texture that is meant to be applied to a 100x100 unit cube should be 1024x1024, as that is the closest power of 2 that matches the project's texture density.

<a name="7.3"></a>
<a name="textures-max-size"></a>
### 7.3 Textures Should Be No Bigger than 8192

No texture should have a dimension that exceeds 8192 in size, unless you have a very explicit reason to do so. Often, using a texture this big is simply just a waste of resources.

<a name="7.4"></a>
<a name="textures-group"></a>
### 7.4 Textures Should Be Grouped Correctly

Every texture has a Texture Group property used for LODing, and this should be set correctly based on its use. For example, all UI textures should belong in the UI texture group.

**[⬆ Back to Top](#table-of-contents)**


## Major Contributors

* [Michael Allar](http://allarsblog.com): [GitHub](https://github.com/Allar), [Twitter](https://twitter.com/michaelallar)
* [CosmoMyzrailGorynych](https://github.com/CosmoMyzrailGorynych)
* [billymcguffin](https://github.com/billymcguffin)
* [akenatsu](https://github.com/akenatsu)

## License

Copyright (c) 2016 Gamemakin LLC

See [LICENSE](/LICENSE)

**[⬆ Back to Top](#table-of-contents)**


## Amendments

We encourage you to fork this guide and change the rules to fit your team's style guide. Below, you may list some amendments to the style guide. This allows you to periodically update your style guide without having to deal with merge conflicts.

# };
