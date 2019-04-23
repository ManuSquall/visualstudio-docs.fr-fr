---
title: Définissez des symboles (.pdb) et les fichiers sources dans le débogueur
ms.custom: seodec18
ms.date: 10/08/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5d7d5fa0a53ead2f49f89df37943d734a1b73fb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045340"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Spécifier les symboles (.pdb) et les fichiers sources dans le débogueur Visual Studio (C#, C++, Visual Basic, F#)

Base de données de programme (*.pdb*) fichiers, également appelés fichiers de symboles, mappent des identificateurs et des instructions dans le code source de votre projet pour les identificateurs correspondants dans compilé des applications.

Lorsque vous générez un projet à partir de l’IDE de Visual Studio avec la norme de configuration de build de débogage, le compilateur crée les fichiers de symboles appropriés. Vous pouvez également [définir les options de symbole dans le code](#compiler-symbol-options).

Le *.pdb* fichier conserve des informations d’état de débogage et de projet qui permet la liaison incrémentielle d’une configuration Debug de votre application. Le débogueur Visual Studio utilise *.pdb* fichiers afin de déterminer les deux éléments clés d’informations pendant le débogage :

* La source fichier nom et numéro de ligne à afficher dans l’IDE Visual Studio.
* Emplacement dans l’application pour s’arrêter pour un point d’arrêt.

Fichiers de symboles indiquent également l’emplacement des fichiers sources et éventuellement, le serveur pour les récupérer à partir de.

Le débogueur charge uniquement *.pdb* les fichiers qui correspondent exactement à la *.pdb* fichiers créés quand une application a été générée (autrement dit, la version d’origine *.pdb* fichiers ou des copies). Cette duplication exacte est nécessaire, car la disposition des applications peut changer même si le code lui-même n’a pas changé. Pour plus d’informations, consultez [Why does Visual Studio require debugger symbol files to *exactly* match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

> [!TIP]
> Pour déboguer le code en dehors de votre code source du projet, telles que le code de Windows ou tiers appelé par votre projet de code, vous devez spécifier l’emplacement du code externe *.pdb* fichiers (et éventuellement, les fichiers sources), qui doit correspondre exactement à les builds dans votre application.

## <a name="symbol-file-locations-and-loading-behavior"></a>Emplacements des fichiers de symboles et le comportement de chargement

> [!NOTE]
> Lorsque vous déboguez du code managé sur un périphérique distant, tous les fichiers de symboles doivent être situés sur l’ordinateur local ou dans un emplacement [spécifié dans les options du débogueur](#BKMK_Specify_symbol_locations_and_loading_behavior).

Lorsque vous déboguez un projet dans l’IDE Visual Studio, le débogueur charge automatiquement les fichiers de symboles qui sont trouvent dans le dossier du projet.

Le débogueur recherche également les fichiers de symboles dans les emplacements suivants :

1. L’emplacement spécifié à l’intérieur de la DLL ou le fichier exécutable (*.exe*) fichier.

   Par défaut, si vous avez créé une DLL ou un *.exe* fichier sur votre ordinateur, l’éditeur de liens place le chemin d’accès complet et le nom de fichier associé *.pdb* fichier dans la DLL ou *.exe* fichier. Le débogueur vérifie si le fichier de symboles existe à cet emplacement.

2. Le même dossier que la DLL ou *.exe* fichier.

3. Tous les emplacements spécifiés dans les options du débogueur pour les fichiers de symboles. Pour ajouter et activer des emplacements de symboles, consultez [configurer des emplacements de symboles et options de chargement](#BKMK_Specify_symbol_locations_and_loading_behavior).

   - Tout dossier de cache de symboles local.

   - Réseau spécifié, internet, ou les serveurs de symboles local et emplacements, tels que les serveurs de symboles Microsoft si sélectionné. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] peut télécharger des fichiers de symboles de débogage à partir de serveurs de symboles qui implémentent le `symsrv` protocole. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) et [outils de débogage pour Windows](/windows-hardware/drivers/debugger/index) sont deux outils qui peuvent utiliser des serveurs de symboles.

     Vous pouvez utiliser des serveurs de symboles sont les suivantes :

     **Serveurs de symboles publics de Microsoft**: Pour déboguer un incident qui se produit lors d’un appel à une DLL système ou à une bibliothèque tierce, vous devez souvent système *.pdb* fichiers. Système *.pdb* fichiers contiennent les symboles pour les DLL de Windows, *.exe* fichiers et pilotes de périphérique. Vous pouvez obtenir les symboles pour les systèmes d’exploitation Windows, MDAC, IIS, ISA et le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] à partir de serveurs de symboles publics de Microsoft.

     **Serveurs de symboles sur un réseau interne ou sur votre ordinateur local** : Votre équipe ou société peut créer les serveurs de symboles de vos propres produits et comme cache des symboles à partir des sources externes. Vous pouvez avoir un serveur de symboles sur votre propre ordinateur.

     **Serveurs de symboles tiers** : Les fournisseurs tiers des applications et des bibliothèques Windows peuvent donner accès au serveur de symboles sur Internet.

     > [!WARNING]
     > Si vous utilisez un serveur de symboles autres que les serveurs de symboles publics Microsoft, assurez-vous que le serveur de symboles et son chemin d’accès sont dignes de confiance. Étant donné que les fichiers de symboles peuvent contenir du code exécutable arbitraire, vous pouvez être exposées aux menaces de sécurité.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Configurer des emplacements de symboles et les options de chargement

Sur le **outils** > **Options** > **débogage** > **symboles** page, vous pouvez :

- Spécifier et sélectionnez des chemins de recherche et serveurs de symboles pour Microsoft, Windows ou composants tiers.
- Spécifier les modules que vous n’ou que vous ne souhaitez pas que le débogueur charge automatiquement des symboles.
- Modifier ces paramètres lorsque vous déboguez activement. Consultez [gérer les symboles lors du débogage](#manage-symbols-while-debugging).

**Pour spécifier des emplacements de symboles et les options de chargement :**

1. Dans Visual Studio, ouvrez **outils** > **Options** > **débogage** > **symboles** (ou **Déboguer** > **Options** > **symboles**).

   ![Outils &#45; Options &#45; débogage &#45; page symboles](media/dbg-options-symbols.png "outils &#45; Options &#45; débogage &#45; page symboles")

2. Sous **emplacements du fichier (.pdb) de symboles**,
   - Pour utiliser le **serveurs de symboles Microsoft**, activez la case à cocher.

   - Pour ajouter un nouvel emplacement du serveur de symbole,
     1. Sélectionnez le **+** symbole dans la barre d’outils.
     1. Dans le champ de texte, tapez le chemin d’accès URL ou un dossier du serveur de symboles ou du magasin de symboles. La saisie semi-automatique des instructions vous aide à rechercher le format correct.

     >[!NOTE]
     >Uniquement dans le dossier spécifié est recherché. Vous devez ajouter des entrées pour tous les sous-dossiers que vous souhaitez rechercher.

   - Pour ajouter un nouvel emplacement de serveur de symboles VSTS
     1. Sélectionnez le ![outils&#47; Options&#47; débogage&#47;icône du nouveau serveur de symboles](media/dbg_tools_options_foldersicon.png "outils &#45; Options &#45; débogage &#45; icône du nouveau serveur de symboles") icône dans la barre d’outils.
     1. Dans le **se connecter au serveur de symboles VSTS** boîte de dialogue, choisissez un des serveurs de symboles disponibles, puis sélectionnez **Connect**.

   - Pour modifier l’ordre de chargement pour les emplacements de symboles, utilisez **Ctrl**+**des** et **Ctrl**+**vers le bas**, ou le **des** et **vers le bas** icônes fléchées.
   - Pour modifier une URL ou un chemin d’accès, double-cliquez sur l’entrée, ou sélectionnez-le et appuyez sur **F2**.
   - Pour supprimer une entrée, sélectionnez-la, puis sélectionnez le **-** icône.

3. (Facultatif) Pour améliorer les performances de chargement de symboles, sous **mettre en Cache les symboles dans ce répertoire**, un chemin d’accès du dossier local qui peuvent copier des serveurs de symboles pour les symboles de type.

   > [!NOTE]
   > Ne placez pas le cache de symboles local dans un dossier protégé, tel que C:\Windows ou un sous-dossier. Utilisez plutôt un dossier en lecture-écriture.

   > [!NOTE]
   > Pour les projets C++, si vous avez le `_NT_SYMBOL_PATH` set variable d’environnement, il remplace la valeur définie sous **mettre en Cache les symboles dans ce répertoire**.

4. Spécifiez les modules que vous souhaitez que le débogueur à charger à partir de la **emplacements du fichier (.pdb) de symboles** lorsqu’il démarre.

   - Sélectionnez **charger tous les modules, sauf exclus** (la valeur par défaut) pour charger tous les symboles pour tous les modules dans l’emplacement du fichier de symboles, à l’exception des modules que vous excluez spécifiquement. Pour exclure certains modules, sélectionnez **spécifier les modules exclus**, sélectionnez le **+** icône, tapez les noms des modules à exclure, puis sélectionnez **OK**.

   - Pour charger uniquement les modules que vous spécifiez à partir des emplacements de fichier de symboles, sélectionnez **charge les modules spécifiés uniquement**. Sélectionnez **spécifier les modules inclus**, sélectionnez le **+** icône, tapez les noms des modules à inclure, puis sélectionnez **OK**. Les fichiers de symboles pour les autres modules ne sont pas chargés.

5. Sélectionnez **OK**.

## <a name="other-symbol-options-for-debugging"></a>Autres options de symbole de débogage

Vous pouvez sélectionner les options de symbole supplémentaires dans **outils** > **Options** > **débogage** > **général** (ou **déboguer** > **Options** > **général**) :

- **Charger les exportations de dll (Natif uniquement)**

  Tables d’exportation de DLL des charges pour C/C++. Pour plus d’informations, consultez [tables d’exportation de DLL](#use-dumpbin-exports). Informations d’exportation de DLL de lecture implique une surcharge, donc le chargement des tables d’exportation est désactivé par défaut. Vous pouvez également utiliser `dumpbin /exports` dans une ligne de commande de génération C/C++.

- **Activer le débogage au niveau de l’adresse** et **afficher le code machine si la source non disponible**

  Affiche toujours le code machine lorsque les fichiers sources ou de symboles sont introuvables.

  ![Options &#47; débogage &#47; général code machine options](../debugger/media/dbg_options_general_disassembly_checkbox.png "Options &#47; débogage &#47; général code machine options")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Activer la prise en charge du serveur source**

  Utilise le serveur Source pour aider à déboguer une application lorsqu’il n’existe pas de code source sur l’ordinateur local, ou le *.pdb* fichier ne correspond pas à du code source. Serveur source prend les demandes de fichiers et retourne les fichiers réels à partir du contrôle de code source. Serveur source s’exécute à l’aide d’une DLL nommée *srcsrv.dll* pour lire l’application *.pdb* fichier. Le *.pdb* fichier contient des pointeurs vers le référentiel de code source, ainsi que les commandes utilisées pour extraire le code source à partir du référentiel.

  Vous pouvez limiter les commandes qui *srcsrv.dll* peuvent exécuter à partir de l’application *.pdb* fichier en répertoriant les commandes autorisées dans un fichier nommé *srcsrv.ini*. Place le *srcsrv.ini* fichier dans le même dossier que *srcsrv.dll* et *devenv.exe*.

  >[!IMPORTANT]
  >Des commandes arbitraires peuvent être incorporées dans une application *.pdb* de fichiers, veillez à placer uniquement les commandes que vous souhaitez exécuter dans un *srcsrv.ini* fichier. Toute tentative d’exécution d’une commande ne se trouvant pas dans le fichier *srcsvr.ini* provoque l’apparition d’une boîte de dialogue de confirmation. Pour plus d’informations, consultez [avertissement de sécurité : le débogueur doit exécuter une commande non approuvée](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >Aucune validation n’est effectuée sur les paramètres de commande, soyez donc prudent avec les commandes de confiance. Par exemple, si vous avez mis *cmd.exe* dans votre *srcsrv.ini*, un utilisateur malveillant peut spécifier des paramètres sur *cmd.exe* qui rendrait dangereux.

  Sélectionnez cet élément et les éléments enfants souhaités. **Autoriser le serveur source pour les assemblys de confiance partielle (managé uniquement)** et **toujours exécuter les commandes du serveur source non fiables sans demander confirmation** peuvent augmenter les risques de sécurité.

  ![Activer les options du serveur source](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>Options de symbole du compilateur

Quand vous générez un projet à partir de l’IDE de Visual Studio avec la norme **déboguer** configuration de build, C++ et les compilateurs managés créent les fichiers de symboles appropriés pour votre code. Vous pouvez également définir des options du compilateur dans le code.

### <a name="cc-options"></a>Options C/C++

- *VC\<x > .pdb* et  *\<projet > .pdb* fichiers

  Un *.pdb* de fichier pour C/C++ est créé quand vous générez avec [/ZI ou /Zi](/cpp/build/reference/z7-zi-zi-debug-information-format). Dans [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], le [/Fd](/cpp/build/reference/fd-program-database-file-name) option noms le *.pdb* le compilateur crée des fichiers. Lorsque vous créez un projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à l’aide de l’IDE, le **/Fd** option est définie pour créer un *.pdb* fichier nommé  *\<projet > .pdb*.

  Si vous générez votre application C/C++ à l’aide d’un makefile, et que vous spécifiez **/Zi** ou **/Zi** sans utiliser **/Fd**, le compilateur crée deux *.pdb*fichiers :

  - *VC\<x.pdb*, où *\<x>* représente la version de Visual C++, par exemple *VC11.pdb*

    Le *VC\<x > .pdb* fichier stocke toutes les informations de débogage pour les fichiers objets individuels et réside dans le même répertoire que le makefile du projet. Chaque fois qu’il crée un fichier objet, le compilateur C/C++ fusionne les informations de débogage dans *VC\<x > .pdb*. Par conséquent, même si chaque fichier source inclut des fichiers d’en-tête courants tels que  *\<windows.h >*, les typedefs de ces en-têtes sont stockés qu’une seule fois, plutôt que dans chaque fichier objet. Les informations insérées incluent les informations de type, mais pas les informations de symbole, comme les définitions de fonctions.

  - *\<project>.pdb*

    Le  *\<projet > .pdb* fichier stocke toutes les informations de débogage pour le projet *.exe* de fichiers et se trouve dans le *\debug* sous-répertoire. Le fichier *\<projet>.pdb* contient toutes les informations de débogage, y compris les prototypes de fonction, et non pas seulement les informations de type présentes dans *VC\<x>.pdb*.

  Les deux le *VC\<x > .pdb* et  *\<projet > .pdb* fichiers autorisent les mises à jour incrémentielles. L’éditeur de liens incorpore également le chemin d’accès à la *.pdb* des fichiers dans le *.exe* ou *.dll* fichier qu’il crée.

- <a name="use-dumpbin-exports"></a>Tables d’exportation de DLL

  Utilisez `dumpbin /exports` pour afficher les symboles disponibles dans la table d’exportation d’une DLL. Informations symboliques de tables d’exportation de DLL peuvent être utiles pour travailler avec les messages Windows, des procédures Windows (WindowProcs), COM des objets, marshaling ou toute DLL que vous n’avez pas les symboles pour. Il existe des symboles pour toutes les DLL système 32 bits. Les appels sont répertoriés dans l'ordre chronologique inverse, la fonction en cours (la plus profondément imbriquée) apparaissant en tête de liste.

  En lisant le `dumpbin /exports` de sortie, vous pouvez voir les noms de fonction exact, y compris les caractères non alphanumériques. Voir les noms de fonction exact est utile pour définir un point d’arrêt sur une fonction, étant donné que les noms de fonction peuvent être tronqués ailleurs dans le débogueur. Pour plus d'informations, consultez [dumpbin /exports](/cpp/build/reference/dash-exports).

### <a name="net-framework-options"></a>Options du .NET Framework

Générer avec **/debug** pour créer un *.pdb* fichier. Vous pouvez générer des applications avec **/debug:full** ou **/debug:pdbonly**. La génération avec **/debug:full** génère du code pouvant être débogué. La génération avec **/debug:pdbonly** permet d’obtenir des fichiers *.pdb*, mais ne génère pas le `DebuggableAttribute` indiquant au compilateur JIT que des informations de débogage sont disponibles. Utilisez **/debug:pdbonly** si vous voulez générer des fichiers *.pdb* pour une version Release sans qu’elle puisse être déboguée. Pour plus d’informations, consultez [/debug (Options du compilateur C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) ou [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).

### <a name="web-applications"></a>Applications Web

Définir le *web.config* fichier de votre application ASP.NET en mode débogage. En mode débogage, ASP.NET génère des symboles pour les fichiers générés dynamiquement et le débogueur peut être attaché à l'application ASP.NET. Visual Studio définit cela automatiquement lorsque vous commencez le débogage, si vous avez créé votre projet à partir du modèle de projets web.

## <a name="manage-symbols-while-debugging"></a>Gérer les symboles lors du débogage

Vous pouvez utiliser la **Modules**, **pile des appels**, **variables locales**, **automatique**, ou n’importe quel **espion** fenêtre à charger symboles ou modifier les options de symbole lors du débogage. Pour plus d’informations, consultez [vous familiariser avec la façon dont le débogueur s’attache à votre application](../debugger/debugger-tips-and-tricks.md#modules_window).

### <a name="use-the-modules-window"></a>Utiliser la fenêtre Modules

Pendant le débogage, le **Modules** fenêtre affiche les modules de code que le débogueur est en traitant comme code de l’utilisateur, ou mon Code et leur état le chargement des symboles. Vous pouvez également surveiller l’état de chargement de symboles, charger des symboles et modifier les options de symbole dans le **Modules** fenêtre.

**Pour surveiller ou modifier des options ou des emplacements de symboles lors du débogage :**

1. Pour ouvrir le **Modules** fenêtre, pendant le débogage, sélectionnez **déboguer** > **Windows** > **Modules**.
1. Dans le **Modules** fenêtre, avec le bouton droit le **état du symbole** ou **fichier de symboles** en-têtes ou n’importe quel module.
1. Dans le menu contextuel, sélectionnez une des options suivantes :

|Option|Description|
|------------|-----------------|
|**Charger les symboles**|S’affiche pour les modules avec des symboles ignorés, introuvables ou non chargés. Tente de charger les symboles d’emplacements spécifiés sur le **Options** > **débogage** > **symboles** page. Si le fichier de symboles est introuvable ou n’a pas chargé, lance **Explorateur de fichiers** afin de pouvoir spécifier un nouvel emplacement de recherche.|
|**Informations sur le chargement de symboles**|Indique l’emplacement d’un fichier de symboles chargé, ou les emplacements de recherche si le débogueur ne peut pas trouver le fichier.|
|**Paramètres des symboles**|Ouvre le **Options** > **débogage** > **symboles** page, où vous pouvez modifier et ajouter des emplacements de symboles.|
|**Toujours charger automatiquement**|Ajoute le fichier de symboles sélectionnés à la liste des fichiers qui sont chargés automatiquement par le débogueur.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Utilisez les pages aucune symboles Loaded/No Source a été chargée

Il existe plusieurs façons pour le débogueur s’arrête dans du code qui n’a pas de fichiers sources ou de symboles disponibles :

- Pas à pas détaillé de code.
- Arrêter dans le code à partir d’un point d’arrêt ou une exception.
- Basculer vers un autre thread.
- Modifier le frame de pile en double-cliquant sur un frame dans la **pile des appels** fenêtre.

Dans ce cas, le débogueur affiche le **chargé des symboles non** ou **aucune Source a été chargée** pages pour vous aider à trouver et charger les symboles nécessaires ou la source.

 ![Aucune page symboles chargés](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**Pour utiliser la page de document aucun symbole chargé pour aider à trouver et charger des symboles manquants :**

- Pour modifier le chemin de recherche, sélectionnez un chemin d’accès non sélectionné, ou **nouveau chemin d’accès** ou **nouveau chemin VSTS** et entrez ou sélectionnez un nouveau chemin d’accès. Sélectionnez **charger** pour effectuer une nouvelle recherche les chemins d’accès et de charger le fichier de symboles s’il est trouvé.
- Pour remplacer les options de symbole et réessayer les chemins de recherche, sélectionnez **Parcourir et rechercher \<exécutable-name >**. Le fichier de symboles est chargé s’il est trouvé, ou **Explorateur de fichiers** s’ouvre pour vous pouvez de sélectionner manuellement le fichier de symboles.
- Pour ouvrir le **Options** > **débogage** > **symboles** page, sélectionnez **modifier les paramètres de symbole**.
- Pour afficher le code machine dans une nouvelle fenêtre une fois, sélectionnez **afficher le code machine**, ou sélectionnez **boîte de dialogue Options** pour définir l’option pour toujours afficher le code machine lorsque les fichiers sources ou de symboles sont introuvables.
- Pour afficher les emplacements de recherche et le résultat, développez **les informations de chargement de symboles**.

Si le débogueur recherche le *.pdb* fichier une fois que vous exécutez une des options et pouvez extraire le fichier source en utilisant les informations dans le *.pdb* fichier, il affiche la source. Sinon, elle affiche un **aucune Source a été chargée** page qui décrit le problème, avec des liens vers les actions susceptibles de résoudre le problème.

**Pour ajouter des chemins de recherche du fichier source à une solution :**

Vous pouvez spécifier les emplacements que le débogueur recherche les fichiers source et exclure des fichiers spécifiques de la recherche.

1. Sélectionnez la solution dans **l’Explorateur de solutions**, puis sélectionnez le **propriétés** icône, appuyez sur **Alt**+**entrée**, ou avec le bouton droit et sélectionnez **propriétés**.

1. Sélectionnez **déboguer les fichiers sources**.

1. Sous **répertoires contenant du code source**, tapez ou sélectionnez les emplacements de code source à rechercher. Utilisez le **nouvelle ligne** icône pour ajouter d’autres emplacements, le **des** et **vers le bas** icônes fléchées pour les réorganiser, ou le **X** icône pour les supprimer.

   >[!NOTE]
   >Le débogueur recherche uniquement dans le répertoire spécifié. Vous devez ajouter des entrées pour tous les sous-répertoires à explorer.

1. Sous **ne pas rechercher ces fichiers sources**, tapez les noms des fichiers sources à exclure de la recherche.

1. Sélectionnez **OK** ou **appliquer**.

## <a name="see-also"></a>Voir aussi
- [Comprendre les fichiers de symboles et les paramètres des symboles de Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Modifications du chargement des symboles distants .NET dans Visual Studio 2012 et 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
