---
title: Analyser les problèmes de mémoire .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e78cefa9778e2889130f865e4c61cc8a97014db7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444658"
---
# <a name="analyze-net-framework-memory-issues"></a>Analyser des problèmes de mémoire liés à .NET Framework
Vous pouvez identifier les fuites et l'utilisation inefficace de la mémoire dans le code .NET Framework à l'aide de l'analyseur de mémoire managée de Visual Studio. La version minimale de .NET Framework du code cible est .NET Framework 4.5.  
  
 Analyse les informations contenues dans l’outil d’analyse de mémoire *fichiers dump avec des données de tas* qui une copie des objets dans la mémoire d’une application. Vous pouvez recueillir des fichiers dump (.dmp) à partir de l'IDE Visual Studio IDE ou à l'aide d'autres outils système.  
  
- Vous pouvez analyser un instantané pour comprendre l’impact relatif des types d’objets sur l’utilisation de la mémoire et pour rechercher le code dans votre application qui utilise la mémoire de manière inefficace.  
  
- Vous pouvez également comparer (*diff*) deux instantanés d’une application pour rechercher les sections de votre code qui provoquent la mémoire permet d’augmenter au fil du temps.  
  
  Pour obtenir une description de l’Analyseur de mémoire managée, consultez [à l’aide de Visual Studio 2013 pour diagnostiquer des problèmes de mémoire .NET en Production](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx) sur Visual Studio ALM + Team Foundation Server blog.  
  
## <a name="BKMK_Contents"></a> Sommaire  
 [Utilisation de la mémoire dans les applications .NET Framework](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identifier un problème de mémoire dans une application](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Collecter les instantanés de mémoire](#BKMK_Collect_memory_snapshots)  
  
 [Analyser l’utilisation de la mémoire](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> Utilisation de la mémoire dans les applications .NET Framework  
 .NET Framework étant un runtime avec Garbage Collection, dans la plupart des applications l'utilisation de la mémoire n'est pas un problème. Par contre, avec les applications de longue durée telles que les applications et les services web, et sur les appareils avec une quantité de mémoire limitée, l'accumulation d'objets en mémoire peut avoir un impact sur les performances de l'application et de l'appareil. Une utilisation excessive de la mémoire peut priver l'application et l'ordinateur de ressources si le garbage collector s'exécute trop souvent ou si le système d'exploitation est contraint de déplacer de la mémoire entre la RAM et le disque. Dans le pire des cas, une application peut se bloquer avec une exception « Mémoire insuffisante ».  
  
 .NET *tas managé* est une région de mémoire virtuelle où sont stockés les objets de référence créés par une application. La durée de vie des objets est gérée par le garbage collector. Le garbage collector utilise des références pour effectuer le suivi des objets qui occupent des blocs de mémoire. Une référence est créée quand un objet est créé et assigné à une variable. Un même objet peut avoir plusieurs références. Par exemple, des références supplémentaires à un objet peuvent être créées en ajoutant l’objet à une classe, une collection ou autre structure de données ou en assignant l’objet à une seconde variable. Une référence peut aussi être créée quand un objet ajoute un gestionnaire à l'événement d'un autre objet. Dans ce cas, le second objet contient la référence au premier jusqu'à ce que le gestionnaire soit supprimé de manière explicite ou que le second objet soit détruit.  
  
 Pour chaque application, le garbage collector tient à jour une arborescence de références qui assure le suivi des objets référencés par l’application. Le *arborescence de références* a un jeu de racines, ce qui inclut des objets globaux et statiques, ainsi que des piles de threads associées et dynamiquement des objets instanciés de. Un objet est enraciné si au moins l'un de ses objets parents y fait référence. Le garbage collector peut récupérer la mémoire d'un objet uniquement quand aucun autre objet ou variable dans l'application n'y fait référence.  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> Identifier un problème de mémoire dans une application  
 Le symptôme le plus visible des problèmes de mémoire est le niveau de performances de votre application, en particulier s'il diminue au fil du temps. Une dégradation des performances d'autres applications pendant que votre application est en cours d'exécution peut également indiquer qu'il existe un problème de mémoire. Si vous suspectez un problème de mémoire, utilisez un outil tel que le Gestionnaire de tâches ou [Analyseur de performances Windows](http://technet.microsoft.com/library/cc749249.aspx) pour approfondir vos recherches. Par exemple, une augmentation de la taille totale de mémoire que vous ne pouvez pas expliquer peut être envisagée comme une source possible de fuites de mémoire :  
  
 ![Croissance constante de la mémoire dans le moniteur de ressource](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Vous pourriez également remarquer des pointes de mémoire plus élevées que ce que votre connaissance du code pourrait suggérer. Cela pourrait être le signe d'une utilisation inefficace de la mémoire dans une procédure :  
  
 ![Pics de mémoire dans le Gestionnaire de ressources](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a> Collecter les instantanés de mémoire  
 Analyse les informations contenues dans l’outil d’analyse de mémoire *fichiers dump* qui contiennent des informations sur le tas. Vous pouvez créer des fichiers de vidage dans Visual Studio, ou vous pouvez utiliser un outil tel que [ProcDump](http://technet.microsoft.com/sysinternals/dd996900.aspx) de [Windows Sysinternals](http://technet.microsoft.com/sysinternals). Consultez [qu’est un fichier de vidage, et comment en créer une ?](http://blogs.msdn.com/b/debugger/archive/2009/12/30/what-is-a-dump-and-how-do-i-create-one.aspx) sur le blog de l’équipe de débogage Visual Studio.  
  
> [!NOTE]
> La plupart des outils peuvent recueillir des informations de dump avec ou sans données de mémoire de tas complètes. L'analyseur de mémoire de Visual Studio nécessite des informations de tas complètes.  
  
 **Pour recueillir un dump à partir de Visual Studio**  
  
1. Vous pouvez créer un fichier dump pour un processus qui a été démarré à partir d'un projet Visual Studio ou vous pouvez attacher le débogueur à un processus en cours d'exécution. Consultez [attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Arrêtez l'exécution. Le débogueur s’arrête lorsque vous choisissez **interrompre tout** sur le **déboguer** menu, ou à une exception, ou à un point d’arrêt  
  
3. Sur le **déboguer** menu, choisissez **enregistrer le Dump sous**. Dans le **enregistrer le Dump sous** boîte de dialogue zone, spécifiez un emplacement et assurez-vous que l’option **Minidump avec segment mémoire** (la valeur par défaut) est sélectionné dans le **enregistrer en tant que type** liste.  
  
   **Pour comparer deux instantanés de mémoire**  
  
   Pour analyser l'augmentation de l'utilisation de la mémoire par une application, recueillez deux fichiers dump à partir d'une même instance de l'application.  
  
   ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a> Analyser l’utilisation de la mémoire  
 [Filtrer la liste des objets](#BKMK_Filter_the_list_of_objects) **&#124;** [analyser les données de mémoire d’un seul instantané](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [comparer deux mémoire captures instantanées](#BKMK_Compare_two_memory_snapshots)  
  
 Pour analyser un fichier dump à la recherche de problèmes de mémoire  
  
1. Dans Visual Studio, choisissez **fichier**, **Open** et spécifiez le fichier de vidage.  
  
2. Sur le **résumé du fichier Minidump** page, choisissez **déboguer la mémoire managée**.  
  
    ![Vider la page Résumé de fichier](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   L'analyseur de mémoire démarre une session de débogage pour analyser le fichier et affiche les résultats dans la page Affichage du tas :  
  
   ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a> Filtrer la liste des objets  
 Par défaut, l'analyseur de mémoire filtre la liste d'objets dans un instantané de la mémoire pour afficher uniquement les types et instances codés par un utilisateur et uniquement les types dont la taille inclusive totale dépasse un seuil de pourcentage de la taille totale du tas. Vous pouvez modifier ces options dans le **afficher les paramètres** liste :  
  
|||  
|-|-|  
|**Activer Uniquement mon code**|Uniquement mon code masque les objets système les plus courants. Ainsi, seuls les types que vous créez figurent dans la liste.<br /><br /> Vous pouvez également définir l’option uniquement mon Code dans Visual Studio **Options** boîte de dialogue. Dans le menu **Déboguer** , choisissez **Options et paramètres**. Dans le **débogage**/**général** onglet, activez ou désactivez **uniquement mon Code**.|  
|**Réduire les petits objets**|**Réduire les petits objets** masque tous les types dont la taille inclusive totale est inférieure à 0,5 % de la taille totale des tas.|  
  
 Vous pouvez également filtrer la liste de types en entrant une chaîne dans le **recherche** boîte. La liste affiche uniquement les types dont le nom contient la chaîne.  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> Analyser les données de mémoire d’un seul instantané  
 Visual Studio démarre une nouvelle session de débogage pour analyser le fichier et affiche les données de mémoire dans une fenêtre Affichage du tas.  
  
 ![La liste Type d’objet](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Table Type d'objet  
 La table du haut mentionne les types d'objets contenus en mémoire.  
  
- **Nombre** indique le nombre d’instances du type dans l’instantané.  
  
- **Taille (octets)** est la taille des instances du type, sans compter la taille des objets auxquels il détient des références à tous les. La clé publique du signataire doit être fournie à la classe  
  
- **Taille inclusive (octets)** inclut les tailles des objets référencés.  
  
  Vous pouvez choisir l’icône des instances (![l’icône d’instance dans la colonne de Type d’objet](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) dans le **Type d’objet** colonne afin d’afficher une liste des instances de la type.  
  
#### <a name="instance-table"></a>Table Instance  
 ![Tableau d’instances](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Instance** est l’emplacement de mémoire de l’objet qui sert d’identificateur d’objet de l’objet  
  
- **Valeur** présente la valeur réelle des types valeur. Vous pouvez placer le pointeur de la souris sur le nom d'un type référence pour afficher ses valeurs de données dans une bulle d'informations.  
  
   ![Instance de valeurs dans une bulle](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Taille (octets)** est la taille de l’objet, sans compter la taille des objets il détient des références. La clé publique du signataire doit être fournie à la classe  
  
- **Taille inclusive (octets)** inclut les tailles des objets référencés.  
  
  Par défaut, les types et les instances sont triés par **taille Inclusive (octets)**. Pour changer l'ordre de tri, choisissez un en-tête de colonne dans la liste.  
  
#### <a name="paths-to-root"></a>Chemins d’accès à la racine  
  
- Pour un type sélectionné dans le **Type d’objet** table, le **chemins d’accès à la racine** tableau montre les hiérarchies de type unique qui mènent aux objets racines pour tous les objets du type, ainsi que le nombre de références à la type qui est au-dessus de lui dans la hiérarchie.  
  
- Pour un objet sélectionné à partir de l’instance d’un type, **chemins d’accès à la racine** affiche un graphique des objets qui contiennent une référence à l’instance. Vous pouvez placer le pointeur de la souris sur le nom de l'objet pour afficher ses valeurs de données dans une bulle d'informations.  
  
#### <a name="referenced-types--referenced-objects"></a>Types référencés / Objets référencés  
  
- Pour un type sélectionné dans le **Type d’objet** table, le **Types référencés** onglet affiche la taille et le nombre de types référencés détenus par tous les objets du type sélectionné.  
  
- Pour une instance sélectionnée d’un type, **objets référencés** affiche les objets qui sont détenues par l’instance sélectionnée. Vous pouvez placer le pointeur de la souris sur le nom pour afficher ses valeurs de données dans une bulle d'informations.  
  
  **Références circulaires**  
  
  Un objet peut faire référence à un second objet qui détient directement ou indirectement une référence au premier objet. Lorsque l’Analyseur de mémoire rencontre cette situation, il cesse d’étendre le chemin d’accès de référence et ajoute un **[Cycle détecté]** annotation à la liste du premier objet et s’arrête.  
  
  **Types racines**  
  
  L'analyseur de mémoire ajoute des annotations aux objets racines qui décrivent le genre de référence détenu :  
  
|Annotation|Description|  
|----------------|-----------------|  
|**Variable statique** `VariableName`|Variable statique. `VariableName` est le nom de la variable.|  
|**Handle de finalisation**|Référence à partir de la file d'attente de finaliseur|  
|**Variable locale**|Variable locale.|  
|**Handle fort**|Handle à une référence forte tiré de la table de handles d'objets.|  
|**Async. Handle épinglé**|Objet épinglé asynchrone tiré de la table de handles d'objets.|  
|**Handle dépendant**|Objet dépendant tiré de la table de handles d'objets.|  
|**Handle épinglé**|Référence forte épinglée tirée de la table de handles d'objets.|  
|**Handle RefCount**|Objet contenant des références tiré de la table de handles d'objets.|  
|**Handle SizedRef**|Handle fort qui conserve une taille approximative de la fermeture collective de tous les objets et racines d’objets au moment du Garbage Collection.|  
|**Variable locale épinglée**|Variable locale épinglée.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a> Comparer deux instantanés de mémoire  
 Vous pouvez comparer deux fichiers dump d'un processus pour rechercher les objets susceptibles de provoquer des fuites de mémoire. L'intervalle entre la collecte du premier fichier (plus ancien) et du second fichier (plus récent) doit être suffisamment élevé pour que l'augmentation du nombre d'objets ayant fuit soit facile à détecter. Pour comparer deux fichiers  
  
1. Ouvrez le fichier de vidage deuxième, puis choisissez **déboguer la mémoire managée** sur le **résumé du fichier Minidump** page.  
  
2. Dans la page de rapport analyse de mémoire, ouvrez le **baseline sélectionnez** liste, puis choisissez **Parcourir** pour spécifier le premier fichier de vidage.  
  
   L’analyseur ajoute des colonnes vers le volet supérieur du rapport qui affichent la différence entre la **nombre**, **taille**, et **taille Inclusive** des types et les valeurs de la instantané antérieur.  
  
   ![Colonnes diff dans la liste type](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   Un **décompte de références Diff** colonne est également ajoutée à la **chemins d’accès à la racine** table.  
  
   ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
## <a name="see-also"></a>Voir aussi  
 [Blog VS ALM TFS : À l’aide de Visual Studio 2013 pour diagnostiquer les problèmes de mémoire .NET en Production](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx)   
 [Channel 9 &#124; Visual Studio TV &#124; analyse de la mémoire managée](http://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; boîte à outils Visual Studio &#124; gérés d’analyse de la mémoire dans Visual Studio 2013](http://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)