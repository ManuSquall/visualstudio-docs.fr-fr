---
title: Définir les fichiers de symboles (. pdb) et les fichiers sources dans le débogueur
description: Découvrez comment configurer et gérer les fichiers de symboles et les fichiers sources dans Visual Studio
ms.custom: ''
ms.date: 3/31/2021
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7ad72d2aa659f3d43bfca99c359d5db94e2d1045
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106083682"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Spécifier des fichiers de symboles (. pdb) et sources dans le débogueur Visual Studio (C#, C++, Visual Basic, F #)

Des fichiers de base de données de programme (*. pdb*), également appelés fichiers de symboles, mappez les identificateurs et les instructions dans le code source de votre projet aux identificateurs et instructions correspondants dans les applications compilées. Ces fichiers de mappage lient le débogueur à votre code source, ce qui permet le débogage.

Quand vous générez un projet à partir de l’IDE de Visual Studio avec la configuration de build Debug standard, le compilateur crée les fichiers de symboles appropriés. Cet article explique comment gérer des fichiers de symboles dans l’IDE, par exemple, comment [spécifier l’emplacement des symboles dans les options du débogueur](#BKMK_Specify_symbol_locations_and_loading_behavior), comment [vérifier l’état du chargement des symboles](#work-with-symbols-in-the-modules-window) pendant le débogage et comment [définir des options de symbole dans le code](#compiler-symbol-options).

Pour obtenir une explication détaillée des fichiers de symboles, consultez les rubriques suivantes :

- [Présentation des fichiers de symboles et des paramètres de symboles Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Pourquoi Visual Studio exige-t-il que les fichiers de symboles du débogueur correspondent exactement aux fichiers binaires avec lesquels ils ont été générés ?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with)

## <a name="how-symbol-files-work"></a>Fonctionnement des fichiers de symboles

Le fichier *. pdb* contient des informations sur l’état du projet et le débogage qui permettent l’édition de liens incrémentielle d’une configuration Debug de votre application. Le débogueur Visual Studio utilise des fichiers *. pdb* pour déterminer deux éléments clés d’informations lors du débogage :

* Nom du fichier source et numéro de ligne à afficher dans l’IDE de Visual Studio.
* Où l’application doit s’arrêter pour un point d’arrêt.

Les fichiers de symboles affichent également l’emplacement des fichiers sources et, éventuellement, le serveur à partir duquel ils doivent être récupérés.

Le débogueur charge uniquement les fichiers *. pdb* qui correspondent exactement aux fichiers *. pdb* créés lors de la génération d’une application (autrement dit, les fichiers *. pdb* d’origine ou les copies). Cette [duplication exacte](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with) est nécessaire, car la disposition des applications peut changer même si le code lui-même n’a pas changé.

> [!TIP]
> Pour déboguer du code en dehors du code source de votre projet, tel que le code Windows ou le code tiers que votre projet appelle, vous devez spécifier l’emplacement des fichiers *. pdb* du code externe (et éventuellement des fichiers sources), qui doivent correspondre exactement aux builds de votre application.

## <a name="symbol-file-locations-and-loading-behavior"></a>Emplacements des fichiers de symboles et comportement de chargement

Quand vous déboguez un projet dans l’IDE de Visual Studio, le débogueur charge automatiquement les fichiers de symboles qui se trouvent dans le dossier du projet.

> [!NOTE]
> Lors du débogage de code managé sur un périphérique distant, tous les fichiers de symboles doivent se trouver sur l’ordinateur local ou à un emplacement [spécifié dans les options du débogueur](#BKMK_Specify_symbol_locations_and_loading_behavior).

Le débogueur recherche également les fichiers de symboles aux emplacements suivants :

1. Emplacement spécifié à l’intérieur de la DLL ou du fichier exécutable (*. exe*).

   Par défaut, si vous avez créé une DLL ou un fichier *. exe* sur votre ordinateur, l’éditeur de liens place le chemin d’accès complet et le nom du fichier. *PDB* associé dans le fichier dll ou *. exe* . Le débogueur vérifie si le fichier de symboles existe dans cet emplacement.

2. Le même dossier que le fichier DLL ou *. exe* .

3. Tous les emplacements spécifiés dans les options du débogueur pour les fichiers de symboles. Pour ajouter et activer des emplacements de symboles, consultez [configurer les emplacements de symboles et les options de chargement](#BKMK_Specify_symbol_locations_and_loading_behavior).

   - Tout dossier de cache de symboles local.

   - Serveurs de symboles réseau, Internet ou locaux spécifiés et emplacements, tels que les serveurs de symboles Microsoft, s’ils sont sélectionnés. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] peut télécharger des fichiers de symboles de débogage à partir des serveurs de symboles qui implémentent le `symsrv` protocole. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) et les [outils de débogage pour Windows](/windows-hardware/drivers/debugger/index) sont deux outils qui peuvent utiliser des serveurs de symboles.

     Les serveurs de symboles que vous pouvez utiliser sont les suivants :

     **Serveurs de symboles publics Microsoft**: pour déboguer un incident qui se produit pendant un appel à une DLL système ou à une bibliothèque tierce, vous avez souvent besoin de fichiers System *. pdb* . Les fichiers System *. pdb* contiennent des symboles pour les dll Windows, les fichiers *. exe* et les pilotes de périphérique. Vous pouvez obtenir des symboles pour les systèmes d’exploitation Windows, MDAC, IIS, ISA et .NET à partir des serveurs de symboles publics Microsoft.

     **Serveurs de symboles sur un réseau interne ou sur votre ordinateur local**: votre équipe ou société peut créer des serveurs de symboles pour vos propres produits et comme cache pour les symboles de sources externes. Vous pouvez avoir un serveur de symboles sur votre propre ordinateur.

     **Serveurs de symboles tiers**: les fournisseurs tiers d’applications et de bibliothèques Windows peuvent fournir un accès au serveur de symboles sur Internet.

     > [!WARNING]
     > Si vous utilisez un serveur de symboles autre que les serveurs de symboles publics Microsoft, assurez-vous que le serveur de symboles et son chemin d’accès sont dignes de confiance. Étant donné que les fichiers de symboles peuvent contenir du code exécutable arbitraire, vous pouvez les exposer à des menaces de sécurité.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Configurer les emplacements de symboles et les options de chargement

Dans la page **Outils**  >  **options** de  >  **débogage**  >   , vous pouvez :

- Spécifiez et sélectionnez des chemins de recherche et des serveurs de symboles pour Microsoft, Windows ou des composants tiers.
- Spécifiez les modules pour lesquels vous voulez que le débogueur charge automatiquement les symboles.
- Modifiez ces paramètres pendant que vous déboguez activement. Consultez [gérer les symboles pendant le débogage](#manage-symbols-while-debugging).

**Pour spécifier les emplacements de symboles et les options de chargement :**

1. Dans Visual Studio, ouvrez **Outils**  >  **options** de  >  **débogage**  >  **symboles** (ou symboles d’options de **débogage**  >    >  ).

2. Sous **emplacements du fichier de symboles (. pdb)**,
   - Pour utiliser les **serveurs de symboles Microsoft** ou le **serveur de symboles NuGet.org**, activez la case à cocher.

   - Pour ajouter un nouvel emplacement de serveur de symboles,
     1. Sélectionnez le **+** symbole dans la barre d’outils.
     1. Tapez l’URL (http), le partage réseau ou le chemin d’accès local du serveur de symboles ou de l’emplacement du symbole dans le champ de texte. La saisie semi-automatique des instructions vous aide à rechercher le format correct.

     ![Outils &#45; options &#45; débogage &#45; page symboles](media/dbg-options-symbols.gif "Outils &#45; options &#45; débogage &#45; page symboles")

     >[!NOTE]
     >Recherche uniquement dans le dossier spécifié. Vous devez ajouter des entrées pour tous les sous-dossiers que vous souhaitez rechercher.

   - Pour ajouter un nouvel emplacement de serveur de symboles VSTS,
     1. Sélectionnez l’icône ![outils&#47; Options&#47; débogage&#47;icône Nouveau serveur symboles](media/dbg_tools_options_foldersicon.png "Outils &#45; options &#45; débogage &#45; icône Nouveau serveur symboles") dans la barre d’outils.
     1. Dans la boîte de dialogue **se connecter au serveur de symboles VSTS** , choisissez l’un des serveurs de symboles disponibles, puis sélectionnez **se connecter**.

   - Pour modifier l’ordre de chargement pour les emplacements de symboles, utilisez **CTRL** + **haut** et **CTRL +** + **bas**, ou les icônes de flèche **haut** et **bas** .
   - Pour modifier une URL ou un chemin d’accès, double-cliquez sur l’entrée ou sélectionnez-la et appuyez sur **F2**.
   - Pour supprimer une entrée, sélectionnez-la, puis sélectionnez l' **-** icône.

3. Facultatif Pour améliorer les performances de chargement de symboles, sous mettre en **cache les symboles dans ce répertoire**, tapez le chemin d’accès au dossier local dans lequel les serveurs de symboles peuvent copier les symboles.

   > [!NOTE]
   > Ne placez pas le cache de symboles local dans un dossier protégé, tel que C:\Windows ou un sous-dossier. Utilisez plutôt un dossier en lecture-écriture.

   > [!NOTE]
   > Pour les projets C++, si la `_NT_SYMBOL_PATH` variable d’environnement est définie, elle remplace la valeur définie sous **symboles du cache dans ce répertoire**.

4. Spécifiez les modules que le débogueur doit charger à partir des **emplacements du fichier de symboles (. pdb)** au démarrage.

   - Sélectionnez **charger tous les modules, sauf s’ils sont exclus** (valeur par défaut) pour charger tous les symboles pour tous les modules dans l’emplacement du fichier de symboles, à l’exception des modules que vous excluez spécifiquement. Pour exclure certains modules, sélectionnez **spécifier les modules exclus**, sélectionnez l' **+** icône, tapez les noms des modules à exclure, puis sélectionnez **OK**.

   - Pour charger uniquement les modules que vous spécifiez à partir des emplacements de fichiers de symboles, sélectionnez **charger uniquement les modules spécifiés**. Sélectionnez **spécifier les modules inclus**, sélectionnez l' **+** icône, tapez les noms des modules à inclure, puis sélectionnez **OK**. Les fichiers de symboles d’autres modules ne sont pas chargés.

5. Sélectionnez **OK**.

## <a name="other-symbol-options-for-debugging"></a>Autres options de symbole pour le débogage

Vous pouvez sélectionner des options de symbole supplémentaires dans **Outils**  >  **options**  >  **débogage**  >  **général** (ou options de **débogage**  >    >  **général**) :

- **Charger les exportations de dll (natif uniquement)**

  Charge les tables d’exportation de DLL pour C/C++. Pour plus d’informations, consultez [dll Export tables](#use-dumpbin-exports). La lecture des informations d’exportation des DLL implique une certaine surcharge. par conséquent, le chargement des tables d’exportation est désactivé par défaut. Vous pouvez également utiliser `dumpbin /exports` dans une ligne de commande de build C/C++.

- **Activer le débogage au niveau** de l’adresse et **afficher le code machine si la source n’est pas disponible**

  Affiche toujours le code machine lorsque les fichiers sources ou de symboles sont introuvables.

  ![Options &#47; débogage &#47; options de désassemblage générales](../debugger/media/dbg_options_general_disassembly_checkbox.png "Options &#47; débogage &#47; options de désassemblage générales")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Activer la prise en charge du serveur source**

  Utilise le serveur source pour déboguer une application quand il n’y a pas de code source sur l’ordinateur local, ou si le fichier *. pdb* ne correspond pas au code source. Le serveur source prend les demandes de fichiers et retourne les fichiers réels du contrôle de code source. Le serveur source s’exécute à l’aide d’une DLL nommée *srcsrv.dll* pour lire le fichier *. pdb* de l’application. Le fichier *. pdb* contient des pointeurs vers le référentiel de code source, ainsi que des commandes utilisées pour extraire le code source du référentiel.

  Vous pouvez limiter les commandes que *srcsrv.dll* pouvez exécuter à partir du fichier *. pdb* de l’application en répertoriant les commandes autorisées dans un fichier nommé *srcsrv.ini*. Placez le fichier *srcsrv.ini* dans le même dossier que *srcsrv.dll* et *devenv.exe*.

  >[!IMPORTANT]
  >Les commandes arbitraires peuvent être incorporées dans le fichier *. pdb* d’une application. par conséquent, veillez à placer uniquement les commandes que vous souhaitez exécuter dans un fichier *srcsrv.ini* . Toute tentative d’exécution d’une commande ne se trouvant pas dans le fichier *srcsvr.ini* provoque l’apparition d’une boîte de dialogue de confirmation. Pour plus d'informations, consultez [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >Aucune validation n’est effectuée sur les paramètres de commande, soyez donc prudent avec les commandes de confiance. Par exemple, si vous avez répertorié *cmd.exe* dans votre *srcsrv.ini*, un utilisateur malveillant peut spécifier des paramètres sur *cmd.exe* qui le rendrait dangereux.

  Sélectionnez cet élément et les éléments enfants de votre choix. **Autoriser le serveur source pour les assemblys de confiance partielle (managé uniquement)** et **toujours exécuter des commandes de serveur source non fiables sans demander de confirmation** peut augmenter les risques de sécurité.

  ![Activer les options du serveur source](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>Options des symboles du compilateur

Quand vous générez un projet à partir de l’IDE de Visual Studio avec la configuration de build **Debug** standard, C++ et les compilateurs managés créent les fichiers de symboles appropriés pour votre code. Vous pouvez également définir des options du compilateur dans le code.

### <a name="net-options"></a>Options .NET

Générez avec **/Debug** pour créer un fichier *. pdb* . Vous pouvez générer des applications avec **/debug:full** ou **/debug:pdbonly**. La génération avec **/debug:full** génère du code pouvant être débogué. La génération avec **/debug:pdbonly** permet d’obtenir des fichiers *.pdb*, mais ne génère pas le `DebuggableAttribute` indiquant au compilateur JIT que des informations de débogage sont disponibles. Utilisez **/debug:pdbonly** si vous voulez générer des fichiers *.pdb* pour une version Release sans qu’elle puisse être déboguée. Pour plus d’informations, consultez [/debug (options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) ou [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).

### <a name="cc-options"></a>Options C/C++

- Fichiers *VC \<x> . pdb* et *\<project> . pdb*

  Un fichier *. pdb* pour C/C++ est créé lorsque vous générez avec [/Zi ou/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format). Dans [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] , l’option [/FD](/cpp/build/reference/fd-program-database-file-name) permet de nommer le fichier *. pdb* créé par le compilateur. Lorsque vous créez un projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à l’aide de l’IDE, l’option **/FD** est définie pour créer un fichier *. pdb* nommé *\<project> . pdb*.

  Si vous générez votre application C/C++ à l’aide d’un Makefile et que vous spécifiez **/Zi** ou **/Zi** sans utiliser **/FD**, le compilateur crée deux fichiers *. pdb* :

  - *VC \<x> . pdb*, où *\<x>* représente la version du compilateur Microsoft C++, par exemple *VC11. pdb*

    Le fichier *VC \<x> . pdb* stocke toutes les informations de débogage pour les fichiers objets individuels et réside dans le même répertoire que le Makefile du projet. À chaque fois qu’il crée un fichier objet, le compilateur C/C++ fusionne les informations de débogage dans *VC \<x> . pdb*. Par conséquent, même si chaque fichier source contient des fichiers d’en-tête communs tels que *\<windows.h>* , les typedefs de ces en-têtes ne sont stockés qu’une seule fois, et non dans chaque fichier objet. Les informations insérées incluent les informations de type, mais pas les informations de symbole, comme les définitions de fonctions.

  - *\<project>.pdb*

    Le fichier *\<project> . pdb* stocke toutes les informations de débogage du fichier *. exe* du projet et réside dans le sous-répertoire *\Debug.* Le fichier *\<project> . pdb* contient des informations de débogage complètes, y compris les prototypes de fonction, pas seulement les informations de type trouvées dans *VC \<x> . pdb*.

  Les fichiers *VC \<x> . pdb* et *\<project> . pdb* autorisent les mises à jour incrémentielles. L’éditeur de liens incorpore également le chemin d’accès aux fichiers *. pdb* dans le fichier. *exe* ou *. dll* qu’il crée.

- <a name="use-dumpbin-exports"></a>Tables d’exportation de DLL

  Utilisez `dumpbin /exports` pour voir les symboles disponibles dans la table d’exportation d’une dll. Les informations symboliques de tables d’exportation de DLL peuvent être utiles pour travailler avec des messages Windows, des procédures Windows (WindowProcs), des objets COM, le marshaling ou toute DLL pour laquelle vous n’avez pas de symboles. Il existe des symboles pour toutes les DLL système 32 bits. Les appels sont répertoriés dans l'ordre chronologique inverse, la fonction en cours (la plus profondément imbriquée) apparaissant en tête de liste.

  En lisant la `dumpbin /exports` sortie, vous pouvez voir les noms exacts des fonctions, y compris les caractères non alphanumériques. L’affichage des noms de fonction exacts est utile pour définir un point d’arrêt sur une fonction, car les noms de fonctions peuvent être tronqués ailleurs dans le débogueur. Pour plus d'informations, consultez [dumpbin /exports](/cpp/build/reference/dash-exports).

### <a name="web-applications"></a>Applications web

Définissez le fichier *web.config* de votre application ASP.net en mode débogage. En mode débogage, ASP.NET génère des symboles pour les fichiers générés dynamiquement et le débogueur peut être attaché à l'application ASP.NET. Visual Studio définit cette valeur automatiquement lorsque vous commencez à déboguer, si vous avez créé votre projet à partir du modèle de projets Web.

## <a name="manage-symbols-while-debugging"></a>Gérer les symboles pendant le débogage

Vous pouvez utiliser la fenêtre **modules**, **pile des appels**, **variables locales**, **automatique** ou n’importe quelle **Espion** pour charger des symboles ou modifier les options de symbole pendant le débogage. Pour plus d’informations, consultez [se familiariser avec la façon dont le débogueur s’attache à votre application](../debugger/debugger-tips-and-tricks.md#modules_window).

### <a name="work-with-symbols-in-the-modules-window"></a>Utiliser des symboles dans la fenêtre Modules

Pendant le débogage, la fenêtre **modules** affiche les modules de code que le débogueur traite en tant que code utilisateur, ou mon code, et leur état de chargement de symboles. Vous pouvez également surveiller l’état du chargement des symboles, charger les symboles et modifier les options de symbole dans la fenêtre **modules** .

**Pour surveiller ou modifier les emplacements de symboles ou les options lors du débogage :**

1. Pour ouvrir la fenêtre **modules** , pendant le débogage, sélectionnez **Déboguer** les  >    >  **modules** Windows (ou appuyez sur **CTRL**  +  **ALT**  +  **U**).
1. Dans la fenêtre **modules** , cliquez avec le bouton droit sur l’en-tête de l' **État du symbole** ou du fichier de **symboles** , ou sur n’importe quel module.
1. Dans le menu contextuel, sélectionnez l’une des options suivantes :

|Option|Description|
|------------|-----------------|
|**Charger les symboles**|S’affiche pour les modules avec des symboles ignorés, introuvables ou non chargés. Tente de charger les symboles à partir des emplacements spécifiés dans la page **options** de  >  **débogage** des options  >   . Si le fichier de symboles est introuvable ou n’est pas chargé, lance l' **Explorateur de fichiers** afin que vous puissiez spécifier un nouvel emplacement dans lequel effectuer la recherche.|
|**Informations sur le chargement de symboles**|Affiche l’emplacement d’un fichier de symboles chargé, ou les emplacements qui ont été recherchés si le débogueur ne peut pas trouver le fichier.|
|**Paramètres des symboles**|Ouvre la page **options** de  >  **débogage**  >   , dans laquelle vous pouvez modifier et ajouter des emplacements de symboles.|
|**Toujours charger automatiquement**|Ajoute le fichier de symboles sélectionné à la liste des fichiers qui sont automatiquement chargés par le débogueur.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Utiliser les pages aucun symbole chargé/aucune source chargée

Il existe plusieurs façons pour le débogueur de s’arrêter dans du code qui n’a pas de fichiers de symboles ou de sources disponibles :

- Pas à pas détaillé dans le code.
- S’arrêter dans le code à partir d’un point d’arrêt ou d’une exception.
- Basculez vers un autre thread.
- Modifiez le frame de pile en double-cliquant sur un frame dans la fenêtre **pile des appels** .

Dans ce cas, le débogueur affiche les pages **aucun symbole chargé** ou **aucune source chargée** pour vous aider à trouver et à charger les symboles ou la source nécessaires.

 ![Page Aucun symbole n’a été chargé](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**Pour utiliser la page de document aucun symbole n’a été chargé pour rechercher et charger les symboles manquants :**

- Pour modifier le chemin de recherche, sélectionnez un chemin d’accès non sélectionné ou sélectionnez **nouveau chemin d'** accès ou **nouveau chemin d’accès VSTS** , puis entrez ou sélectionnez un nouveau chemin d’accès. Sélectionnez **charger** pour rechercher à nouveau les chemins d’accès et charger le fichier de symboles s’il est trouvé.
- Pour remplacer toutes les options de symbole et réessayer les chemins de recherche, sélectionnez **Parcourir et rechercher \<executable-name>**. Le fichier de symboles est chargé s’il est trouvé, ou l' **Explorateur de fichiers** s’ouvre pour vous permettre de sélectionner manuellement le fichier de symboles.
- Pour ouvrir la page Paramètres de symbole pour configurer le comportement, sélectionnez **modifier les paramètres de symbole** (ou choisissez **options** de  >  **débogage**  >  **symboles**).
- Détaillées Pour afficher le code machine dans une nouvelle fenêtre une fois, sélectionnez **afficher le code machine** ou sélectionnez **boîte de dialogue Options** pour définir l’option permettant d’afficher toujours le code machine lorsque les fichiers sources ou de symboles sont introuvables. Pour plus d’informations, consultez [afficher le code machine](../debugger/how-to-use-the-disassembly-window.md).
- Pour afficher les emplacements recherchés et le résultat, développez **informations sur le chargement des symboles**.
- Pour le code C#, vous pouvez également choisir de [décompiler le code source](../debugger/decompilation.md) des pages **aucun symbole chargé** ou **aucune source chargée** .

Si le débogueur trouve le fichier *. pdb* après l’exécution de l’une des options et peut récupérer le fichier source à l’aide des informations contenues dans le fichier *. pdb* , il affiche la source. Dans le cas contraire, il affiche une page **aucune source chargée** qui décrit le problème, avec des liens vers des actions susceptibles de résoudre le problème.

**Pour ajouter des chemins de recherche de fichier source à une solution :**

Vous pouvez spécifier les emplacements où le débogueur recherche les fichiers sources et exclure des fichiers spécifiques de la recherche.

1. Sélectionnez la solution dans **Explorateur de solutions**, puis sélectionnez l’icône **Propriétés** , appuyez sur **ALT** + **entrée**, ou cliquez avec le bouton droit et sélectionnez **Propriétés**.

1. Sélectionnez **fichiers sources pour le débogage**.

   ![Page fichiers sources pour le débogage](../debugger/media/dbg-source-files.png)

1. Sous **répertoires contenant du code source**, tapez ou sélectionnez les emplacements de code source à rechercher. Utilisez l’icône **nouvelle ligne** pour ajouter d’autres emplacements, les icônes de direction **haut** et **bas** pour les réorganiser, ou l’icône **X** pour les supprimer.

   >[!NOTE]
   >Le débogueur effectue une recherche uniquement dans le répertoire spécifié. Vous devez ajouter des entrées pour tous les sous-répertoires à explorer.

1. Sous **ne pas rechercher ces fichiers sources**, tapez les noms des fichiers sources à exclure de la recherche.

1. Sélectionnez **OK** ou **appliquer**.

## <a name="see-also"></a>Voir aussi
- [Présentation des fichiers de symboles et des paramètres de symboles Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Modifications du chargement des symboles distants .NET dans Visual Studio 2012 et 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)