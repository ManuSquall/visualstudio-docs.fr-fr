---
title: Spécifier les symboles (.pdb) et les fichiers sources dans le débogueur Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adc5dc9be50055417ecb5136f3d3640144c5d69a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733545"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger"></a>Spécifiez les fichiers de symbole (.pdb) et les fichiers source dans le débogueur Visual Studio.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un fichier de base de données du programme (.pdb), également appelé fichier de symboles, mappe les identificateurs que vous créez dans les fichiers sources pour les classes, méthodes et autre code aux identificateurs utilisés dans les fichiers exécutables compilés de votre projet. Le fichier .pdb mappe également les instructions du code source aux instructions d'exécution des fichiers exécutables. Le débogueur utilise ces informations pour déterminer deux informations essentielles : le fichier source et le numéro de ligne qui s'affichent dans l'IDE de Visual Studio et l'emplacement où s'arrêter dans le fichier exécutable lorsque vous définissez un point d'arrêt. Un fichier de symboles contient également l'emplacement d'origine des fichiers sources, et éventuellement, l'emplacement d'un serveur source d'où les fichiers sources peuvent être extraits.  
  
 Quand vous déboguez un projet dans l’IDE de Visual Studio, le débogueur connaît l’emplacement par défaut des fichiers .pdb et des fichiers sources de votre code. Si vous souhaitez déboguer du code en dehors du code source de votre projet, tel que le code Windows ou tiers appelé par votre projet, vous devez spécifier l'emplacement du fichier .pdb (et éventuellement, des fichiers sources du code externe) et ces fichiers doivent correspondre exactement à la build des fichiers exécutables.  
  
 Avant Visual Studio 2012, quand vous déboguiez du code managé sur un appareil distant, vous deviez placer les fichiers de symboles sur l’ordinateur distant. Ce n'est désormais plus le cas. Tous les fichiers de symboles doivent se trouver sur l’ordinateur local ou à un emplacement spécifié dans la page **Outils / Options / Débogage / Symboles** .  
  
##  <a name="BKMK_Find_symbol___pdb__files"></a> Où le débogueur recherche les fichiers .pdb  
  
1.  Emplacement spécifié à l'intérieur de la DLL ou du fichier exécutable.  
  
     (Par défaut, si vous avez développé une DLL ou un fichier exécutable sur votre ordinateur, l'éditeur de liens place le chemin d'accès complet et le nom du fichier .pdb associé à l'intérieur de la DLL ou du fichier exécutable. Le débogueur vérifie d'abord si le fichier de symboles existe dans l'emplacement spécifié dans la DLL ou le fichier exécutable. Cela est utile, car vous avez toujours des symboles disponibles pour le code que vous avez compilé sur votre ordinateur.)  
  
2.  fichiers .pdb qui peuvent être présents dans le même dossier que la DLL ou le fichier exécutable.  
  
3.  Tout dossier de cache de symboles local.  
  
4.  Tout serveur de symboles réseau, internet ou local et tout emplacement sur lequel il sont spécifiés, comme le serveur de symboles Microsoft s'il est activé.  
  
###  <a name="BKMK_Why_do_symbol_files_need_to_exactly_match_the_executable_files_"></a> Pourquoi les fichiers de symboles doivent-ils correspondre exactement aux fichiers exécutables ?  
 Le débogueur chargera uniquement un fichier .pdb pour un fichier exécutable qui correspond exactement au fichier .pdb créé lors de la génération du fichier exécutable (autrement dit, le fichier .pdb doit être le fichier d'origine ou une copie du fichier .pdb d'origine). Étant donné que le compilateur est optimisé pour la vitesse de compilation en plus de sa tâche principale qui consiste à créer du code correct et efficace, la disposition effective d’un fichier exécutable peut changer même si le code lui-même n’a pas changé. Pour plus d’informations, consultez l’entrée de blog intitulée [Why does Visual Studio require debugger symbol files to *exactly* match the binary files that they were built with? (Pourquoi Visual Studio exige-t-il que les fichiers de symboles du débogueur correspondent exactement aux fichiers binaires avec lesquels ils ont été créés ?)](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/).  
  
###  <a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a> Spécifier des emplacements de symboles et le comportement de chargement  
 Lorsque vous déboguez un projet dans l'IDE de Visual Studio, le débogueur charge automatiquement les fichiers de symboles situés dans le répertoire du projet. Vous pouvez spécifier d’autres chemins de recherche et serveurs de symboles pour les composants Microsoft, Windows, ou composants tiers dans **Outils / Options / Débogage / Symboles**. Vous pouvez également spécifier des modules spécifiques pour lesquels vous souhaitez que le débogueur charge automatiquement des symboles. Et vous pouvez ensuite modifier ces paramètres manuellement lorsque vous déboguez activement.  
  
1. Dans Visual Studio, ouvrez la page **Outils / Options / Débogage / Symboles** .  
  
    ![Outils &#45; Options &#45; débogage &#45; page symboles](../debugger/media/dbg-tools-options-symbols.png "DBG_Tools_Options_Symbols")  
  
2. Choisissez le dossier ![outils&#47; Options&#47; débogage&#47;icône de dossier de symboles](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") icône. Le texte modifiable s'affiche dans la zone **Emplacements du fichier de symboles (.pdb)** .  
  
3. Tapez l'URL ou le chemin d'accès du serveur de symboles ou de l'emplacement de symboles. La saisie semi-automatique des instructions vous aide à rechercher le format correct.  
  
4. Pour améliorer les performances de chargement de symboles, tapez le chemin d'accès d'un répertoire local dans lequel les symboles peuvent être copiés par les serveurs de symboles dans la zone **Mettre en cache les symboles dans ce répertoire** d'un répertoire local dans lequel les symboles peuvent être copiés.  
  
   > [!NOTE]
   >  Ne placez pas votre cache de symboles dans un dossier protégé (tel que le dossier C:\Windows ou un de ses sous-dossiers). Utilisez plutôt un dossier en lecture-écriture.  
  
   **Spécifier le comportement de chargement des symboles**  
  
   Vous pouvez spécifier les fichiers qui doivent être chargés automatiquement à partir des emplacements de zone **Emplacements du fichier de symboles (.pdb)** lorsque vous commencez le débogage. Les fichiers de symboles contenus dans le répertoire du projet sont toujours chargés.  
  
5. Sélectionnez **Tous les modules, sauf exclus** pour charger tous les symboles pour tous les modules à l'exception de ceux que vous spécifiez lorsque vous choisissez le lien **Spécifier les modules exclus** .  
  
6. Choisissez l'option **Modules spécifiés uniquement** puis choisissez **Spécifier les modules** pour répertorier les modules des fichiers de symboles que vous voulez charger automatiquement. Les fichiers de symboles d'autres modules sont ignorés.  
  
   **Spécifiez les options de symbole supplémentaires**  
  
   Vous pouvez également définir les options suivantes dans la page **Outils / Options / Débogage / Symboles** :  
  
   **Avertir si aucun symbole au lancement (natif uniquement)**  
  
   Lorsqu'elle est sélectionnée, cette option affiche une boîte de dialogue d'avertissement quand vous essayez de déboguer un programme pour lequel le débogueur ne possède aucune information symbolique.  
  
   **Charger les exportations de DLL**  
  
   Lorsqu'elle est sélectionnée, cette option charge les tables d'exportation de DLL. Les informations symboliques de tables d'exportation de DLL peuvent être utiles si vous utilisez des messages Windows, des procédures Windows (WindowProcs), des objets COM, le marshaling ou toute DLL pour laquelle vous n'avez pas de symbole. La lecture des informations d'exportation des DLL implique une certaine charge mémoire. Par conséquent, cette fonctionnalité est désactivée par défaut.  
  
   Pour savoir quels symboles sont disponibles dans la table d'exportation d'une DLL, utilisez `dumpbin /exports`. Il existe des symboles pour toutes les DLL système 32 bits. En lisant le résultat de `dumpbin /exports` , vous apprenez le nom exact de la fonction, y compris les caractères non alphanumériques. Cette information peut être utile pour définir un point d'arrêt sur une fonction. Les noms de fonctions provenant de tables d'exportation de DLL peuvent s'afficher sous une forme tronquée dans les autres parties du débogueur. Les appels sont répertoriés dans l'ordre chronologique inverse, la fonction en cours (la plus profondément imbriquée) apparaissant en tête de liste. Pour plus d'informations, consultez [dumpbin /exports](http://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).  
  
###  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a> Utiliser des serveurs de symboles pour rechercher des fichiers de symboles qui ne sont pas sur votre ordinateur local  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] peut télécharger les fichiers de symboles de débogage à partir des serveurs de symboles qui implémentent le protocole symsrv. [Visual Studio Team Foundation Server](http://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6) et les [outils de débogage pour Windows](http://msdn.microsoft.com/library/windows/hardware/ff551063\(v=VS.85\).aspx) sont deux outils qui peuvent implémenter des serveurs de symboles. Vous spécifiez les serveurs de symboles à utiliser dans la boîte de dialogue **Options** de Visual Studio.  
  
 Les serveurs de symboles que vous pouvez utiliser sont les suivants :  
  
 **Serveurs de symboles publics Microsoft**  
  
 Pour déboguer un incident survenu durant un appel à une DLL système ou une bibliothèque tierce, vous devrez souvent utiliser des fichiers .pdb système, qui contiennent les symboles des fichiers DLL, EXE et pilotes de périphériques de Windows. Vous pouvez obtenir ces symboles auprès des serveurs de symboles publics Microsoft. Les serveurs de symboles publics Microsoft fournissent des symboles pour les systèmes d'exploitation Windows, en plus de MDAC, d'IIS, d'ISA et du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 Pour utiliser les serveurs de symboles Microsoft, choisissez **Options et paramètres** dans le menu **Déboguer** , puis choisissez **Symboles**. Sélectionnez **Serveurs de symboles Microsoft**.  
  
 **Serveurs de symboles sur un réseau interne ou sur votre ordinateur local**  
  
 Votre équipe ou société peut créer les serveurs de symboles de vos propres produits et comme cache des symboles à partir des sources externes. Vous pouvez avoir un serveur de symboles sur votre propre ordinateur. Vous pouvez entrer l'emplacement des serveurs de symboles en tant qu'URL ou comme chemin sur la page **Débogage**/**Symboles** de la **boîte de dialogue Options**.  
  
 **Serveurs de symboles tiers**  
  
 Les fournisseurs tiers des applications et des bibliothèques Windows peuvent donner accès au serveur de symboles sur Internet. Vous entrez également l'URL de ces serveurs de symboles sur la page **Débogage**/**Symboles** ,  
  
> [!NOTE]
>  Si vous utilisez un serveur de symboles autre que les serveurs de symboles publics Microsoft, assurez-vous que ce serveur et son chemin d'accès sont dignes de confiance. Étant donné que les fichiers de symboles peuvent contenir du code exécutable arbitraire, vous vous exposez à des menaces de sécurité.  
  
###  <a name="BKMK_Find_and_load_symbols_while_debugging"></a> Rechercher et charger des symboles pendant le débogage  
 Lorsque le débogueur est en mode arrêt, vous pouvez charger des symboles pour un module qui a été précédemment exclu par les options du débogueur ou que le compilateur n'a pas pu trouver. Vous pouvez charger les symboles à partir des menus contextuels des fenêtres Pile des appels, Modules, Variables locales, Automatique et Espion. Si le débogueur s'arrête dans du code qui ne contient pas de fichiers sources ou de symboles disponibles, une fenêtre de document s'affiche. Vous trouverez des informations sur les fichiers manquants et pourrez prendre des mesures pour les localiser et les charger.  
  
 **Rechercher des symboles à l'aide des pages de document Aucun symbole n'a été chargé**  
  
 Il existe plusieurs moyens pour que le débogueur se divise en code n'ayant pas de symboles disponibles :  
  
1. Codage en mode pas à pas détaillé.  
  
2. Arrêt dans le code depuis un point d'arrêt ou une exception.  
  
3. Passage à un autre thread.  
  
4. Modification du frame de pile en double-cliquant sur un frame dans la fenêtre Pile des appels.  
  
   Lorsqu'un de ces événements se produit, le débogueur affiche la page **Aucun symbole n'a été chargé** pour vous aider à identifier et à charger les symboles nécessaires.  
  
   ![Aucune page symboles chargés](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")  
  
- Pour modifier les chemins de recherche, choisissez un chemin d'accès non sélectionné ou choisissez **Nouveau** et entrez un nouveau chemin d'accès. Sélectionnez **Charger** pour rechercher à nouveau les chemins d'accès et charger le fichier de symboles s'il est trouvé.  
  
- Choisissez **Parcourir et rechercher**_nom_exécutable_**...** pour remplacer toutes les options de symbole et réessayer les chemins de recherche. Le fichier de symboles est chargé s'il est trouvé, ou un Explorateur de fichiers s'affiche pour sélectionner manuellement le fichier de symboles.  
  
- Sélectionnez **Modifier les paramètres des symboles ...** pour afficher la page **Débogage** / **Symboles** de la boîte de dialogue Options de VS.  
  
- Choisissez **afficher le code machine** pour afficher le code machine dans une nouvelle fenêtre.  
  
- Pour toujours afficher le code machine lorsque la source ou les fichiers de symboles sont introuvables, choisissez le lien **Boîte de dialogue Options** , puis sélectionnez **Activer le débogage au niveau de l'adresse** et **Afficher le code machine si la source n'est pas disponible**.  
  
   ![Options &#47; débogage &#47; général code machine options](../debugger/media/dbg-options-general-disassembly-checkbox.png "DBG_Options_General_disassembly_checkbox")  
  
  **Changer les options de symbole depuis le menu contextuel**  
  
  Lorsque vous êtes en mode arrêt, vous pouvez rechercher et charger les symboles des éléments affichés dans les fenêtres Pile des appels, Modules, Variables locales, Automatique et Espion. Sélectionnez un élément dans la fenêtre, ouvrez le menu contextuel, puis sélectionnez l'une des options suivantes :  
  
|Option|Description|  
|------------|-----------------|  
|**Charger les symboles**|Essaie de charger les symboles d'emplacements spécifiés sur la page **Débogage** / **Symboles** de la boîte de dialogue **Options** de Visual Studio. Si le fichier de symboles est introuvable, l'Explorateur de fichiers est lancé afin que vous puissiez spécifier un nouvel emplacement de recherche.|  
|**Informations sur le chargement de symboles**|Présente des informations indiquant l'emplacement d'un fichier de symboles chargé, ou les emplacements ayant fait l'objet d'une recherche si le débogueur ne trouve pas le fichier.|  
|**Paramètres des symboles...**|Ouvre la page **Débogage** / **Symboles** de la **Options** de Visual Studio.|  
|**Toujours charger automatiquement**|Ajoute le fichier de symboles à la liste des fichiers qui sont automatiquement chargés par le débogueur.|  
  
###  <a name="BKMK_Set_compiler_options_for_symbol_files"></a> Définir des options du compilateur pour les fichiers de symboles  
 Lorsque vous générez votre projet à partir du VS IDE et utilisez la configuration de build **Debug** standard, C++ et les compilateurs managés créent les fichiers de symboles appropriés pour votre code. Vous pouvez aussi définir les options du compilateur sur la ligne de commande pour créer les fichiers de symboles.  
  
 **Options C++**  
  
 Un fichier .pdb (base de données du programme) contient des informations sur l'état du projet et le débogage, qui permettent l'édition des liens incrémentielle pour la configuration Debug de votre programme. Un fichier .pdb est créé lors de la génération à l'aide de [/ZI ou /Zi](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) (pour C/C++).  
  
 Dans [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], l'option [/Fd](http://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a) permet de nommer le fichier .pdb créé par le compilateur. Quand vous créez un projet dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] à l’aide des Assistants, l’option **/Fd** est définie pour créer un fichier .pdb nommé *projet*.pdb.  
  
 Si vous générez votre application C/C++ à l’aide d’un makefile et que vous spécifiez **/ZI** ou **/Zi** sans **/Fd**, vous obtenez finalement deux fichiers .pdb :  
  
- VC*x*.pdb, où *x* représente la version de Visual C++, par exemple VC11.pdb. Ce fichier stocke toutes les informations de débogage concernant les fichiers OBJ individuels et réside dans le même répertoire que le makefile du projet.  
  
- project.pdb   Ce fichier stocke toutes les informations de débogage concernant le fichier .exe. Pour C/C++, il réside dans le sous-répertoire \debug.  
  
  Chaque fois qu'il crée un fichier OBJ, le compilateur C/C++ fusionne les informations de débogage dans VC*x*.pdb. Celles-ci se composent d'informations de type, mais pas d'informations de symbole telles que les définitions de fonctions. Par conséquent, même si chaque fichier source inclut des fichiers d’en-tête courants tels que \<windows.h >, les typedefs de ces en-têtes sont stockés une seule fois, au lieu d’être pour chaque fichier OBJ.  
  
  L'Éditeur de liens crée projet.pdb, qui contient les informations de débogage concernant le fichier EXE du projet. Le fichier projet.pdb contient toutes les informations de débogage, y compris les prototypes de fonction et pas seulement les informations de type présentes dans VC*x*.pdb. Les deux fichiers .pdb autorisent les mises à jour incrémentielles. L'Éditeur de liens incorpore également le chemin d'accès au fichier .pdb dans le fichier .exe ou .dll qu'il crée.  
  
  Le débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utilise le chemin d'accès au fichier .pdb dans le fichier EXE ou DLL pour rechercher le fichier project.pdb. Si le débogueur ne peut pas trouver le fichier .pdb à cet emplacement ou que le chemin d'accès n'est pas valide (par exemple, lorsque le projet a été déplacé sur un autre ordinateur), le débogueur recherche le chemin d'accès contenant le fichier EXE, les chemins d'accès aux symboles spécifiés dans la boîte de dialogue **Options** (dossier**Débogage** , nœud **Symboles** ). Le débogueur ne chargera pas un fichier .pdb qui ne correspond pas au fichier exécutable débogué. Si le débogueur ne trouve aucun fichier .pdb, la boîte de dialogue **Rechercher des symboles** qui s'affiche vous permet de rechercher des symboles ou d'ajouter des emplacements supplémentaires au chemin de recherche.  
  
  **Options du .NET Framework**  
  
  Un fichier .pdb (base de données du programme) contient des informations sur l'état du projet et le débogage, qui permettent l'édition des liens incrémentielle pour la configuration Debug de votre programme. Un fichier .pdb est créé quand vous générez avec **/debug**. Vous pouvez générer des applications avec **/debug:full** ou **/debug:pdbonly**. La génération avec **/debug:full** génère du code pouvant être débogué. La génération avec **/debug:pdbonly** permet d’obtenir des fichiers .pdb mais ne génère pas le `DebuggableAttribute` indiquant au compilateur JIT que des informations de débogage sont disponibles. Utilisez **/debug:pdbonly** si vous souhaitez générer des fichiers .pdb pour une version Release sans qu’elle puisse être déboguée. Pour plus d'informations, consultez [/debug (C# Compiler Options)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969) ou [/debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).  
  
  Le débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utilise le chemin d'accès au fichier .pdb dans le fichier EXE ou DLL pour rechercher le fichier project.pdb. Si le débogueur ne peut pas trouver le fichier .pdb à cet emplacement ou si le chemin d'accès n'est pas valide, le débogueur recherche le chemin d'accès qui contient l'EXE, puis les chemins d'accès aux symboles spécifiés dans la boîte de dialogue **Options** . Ce chemin d'accès est en général le dossier **Débogage** du nœud **Symboles** . Le débogueur ne chargera pas un fichier .pdb qui ne correspond pas au fichier exécutable débogué. Si le débogueur ne trouve aucun fichier .pdb, la boîte de dialogue **Rechercher des symboles** qui s'affiche vous permet de rechercher des symboles ou d'ajouter des emplacements supplémentaires au chemin de recherche.  
  
  **Applications Web**  
  
  Le fichier de configuration de votre application (Web.config) doit avoir pour valeur mode débogage. En mode débogage, ASP.NET génère des symboles pour les fichiers générés dynamiquement et le débogueur peut être attaché à l'application ASP.NET. VS définit cela automatiquement lorsque vous commencez le débogage, si vous avez créé votre projet à partir du modèle de projets web.  
  
##  <a name="BKMK_Find_source_files"></a> Rechercher les fichiers sources  
  
###  <a name="BKMK_Where_the_debugger_searches_for_source_files"></a> Où le débogueur recherche les fichiers source  
 Le débogueur recherche des fichiers sources dans les emplacements suivants :  
  
1.  Fichiers ouverts dans l'IDE de l'instance Visual Studio qui a lancé le débogueur.  
  
2.  Fichiers dans la solution ouverte dans l’instance Visual Studio.  
  
3.  Répertoires qui sont spécifiés dans la page **Propriétés communes** / **Fichiers sources pour le débogage** dans les propriétés de la solution. (Dans le l’ **Explorateur de solutions**, sélectionnez le nœud de la solution, cliquez dessus avec le bouton droit, puis sélectionnez **Propriétés**. )  
  
4.  Informations sources du .pdb du module. Il peut s'agir de l'emplacement du fichier source lorsque le module a été généré, ou d'une commande d'un serveur source.  
  
###  <a name="BKMK_Find_and_load_source_files_with_the_No_Source___No_Symbols_Loaded_pages"></a> Rechercher et charger des fichiers sources à l'aide des pages Aucune source / Aucun symbole n'a été chargé  
 Lorsque le débogueur interrompt l'exécution à un emplacement où le fichier source n'est pas disponible, il affiche les pages **Aucune source n'a été chargée** ou **Aucun symbole n'a été chargé** qui peuvent vous aider à trouver le fichier source. Le message **Aucun symbole n'a été chargé** apparaît lorsque le débogueur ne trouve aucun fichier de symboles (.pdb) pour le fichier exécutable pour terminer sa recherche. La page Aucun symbole fournit des options de recherche pour le fichier. Si le fichier .pdb est trouvé après l'exécution d'une des options et que le débogueur peut récupérer le fichier source à l'aide des informations contenues dans le fichier de symboles, la source est affichée. Sinon, la page **Aucune source n'a été chargée** apparaît et décrit le problème. La page affiche les liens d'option qui peuvent effectuer des actions pouvant résoudre le problème.  
  
###  <a name="BKMK_Add_source_file_search_paths_to_a_solution"></a> Ajouter des chemins de recherche de fichier source à une solution  
 Vous pouvez spécifier le réseau ou les répertoires locaux sur lesquels rechercher les fichiers sources.  
  
1. Sélectionnez la solution dans l'Explorateur de solutions, puis choisissez **Propriétés** dans le menu contextuel.  
  
2. Sous le nœud **Propriétés communes** , choisissez **Fichiers sources pour le débogage**.  
  
3. Cliquez sur le dossier ![outils&#47; Options&#47; débogage&#47;icône de dossier de symboles](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") icône. Le texte modifiable apparaît dans la liste **Répertoires contenant du code source** .  
  
4. Ajoutez le chemin que vous souhaitez rechercher.  
  
   Notez que seul le répertoire spécifié est recherché. Vous devez ajouter des entrées pour tous les sous-répertoires à explorer.  
  
###  <a name="BKMK_Use_source_servers"></a> Utiliser des serveurs sources  
 Lorsqu'il n'y a pas de code source sur l'ordinateur local ou si le fichier .pdb ne correspond pas au code source, le serveur source peut vous aider à déboguer une application. Il prend les demandes de fichiers et retourne les fichiers réels. Le serveur source s'exécute au moyen d'un fichier DLL nommé srcsrv.dll. Le serveur source lit le fichier .pdb de l'application, qui contient des pointeurs vers le référentiel de code source ainsi que des commandes utilisées pour extraire le code source du référentiel. Vous pouvez limiter les commandes dont vous autorisez l'exécution et appartenant au fichier .pdb de l'application en les répertoriant dans un fichier srcsrv.ini qui doit se trouver dans le même répertoire que srcsrv.dll et devenv.exe.  
  
> [!IMPORTANT]
>  Les commandes arbitraires peuvent être incorporées dans le fichier .pdb de l'application, veillez à ne mettre que celles que vous voulez exécuter dans le fichier srcsrv.ini. Toute tentative d'exécution d'une commande ne se trouvant pas dans le fichier srcsvr.ini provoque l'apparition d'une boîte de dialogue de confirmation. Pour plus d'informations, consultez [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Aucune validation n’est effectuée sur les paramètres de commande, soyez donc prudent avec les commandes de confiance. Par exemple, vous avez confiance en cmd.exe, mais un utilisateur malveillant a pu spécifier des paramètres qui rendent la commande dangereuse.  
  
 **Pour activer l'utilisation d'un serveur source**  
  
1.  Vérifiez que vous respectez les mesures de sécurité décrites dans la section précédente.  
  
2.  Dans le menu **Outils** , choisissez **Options**.  
  
     La boîte de dialogue **Options** s'affiche.  
  
3.  Dans le nœud **Débogage** , choisissez la page **Général**.  
  
4.  Activez la case à cocher **Activer le support du serveur source** .  
  
     ![Activer les options du serveur source](../debugger/media/dbg-options-general-enablesrcsrvr-checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")  
  
5.  (Facultatif) Sélectionnez les options enfants que vous souhaitez.  
  
     Notez que les deux options **Autoriser le serveur source pour les assemblys de confiance partielle (managé uniquement)** et **Toujours exécuter les commandes de serveur source non fiables sans demander de confirmation** peuvent augmenter les risques de sécurité décrits ci-dessus.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications du chargement des symboles distants .NET dans Visual Studio 2012 et 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)





