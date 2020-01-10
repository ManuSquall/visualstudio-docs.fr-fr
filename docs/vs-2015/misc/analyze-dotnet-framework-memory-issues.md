---
title: Analyser les problèmes de mémoire d' .NET Framework | Microsoft Docs
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
ms.openlocfilehash: e94edbeac381ac634171507766126ab954153eb1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295889"
---
# <a name="analyze-net-framework-memory-issues"></a>Analyser des problèmes de mémoire liés à .NET Framework
Vous pouvez identifier les fuites et l'utilisation inefficace de la mémoire dans le code .NET Framework à l'aide de l'analyseur de mémoire managée de Visual Studio. La version minimale de .NET Framework du code cible est .NET Framework 4.5.  
  
 L’outil d’analyse de la mémoire analyse les informations des *fichiers dump avec les données de segment* de mémoire qu’une copie des objets dans la mémoire d’une application. Vous pouvez recueillir des fichiers dump (.dmp) à partir de l'IDE Visual Studio IDE ou à l'aide d'autres outils système.  
  
- Vous pouvez analyser un instantané pour comprendre l’impact relatif des types d’objets sur l’utilisation de la mémoire et pour rechercher le code dans votre application qui utilise la mémoire de manière inefficace.  
  
- Vous pouvez également comparer (*diff*) deux instantanés d’une application pour rechercher des zones de votre code qui entraînent une augmentation de l’utilisation de la mémoire au fil du temps.  
  
  Pour obtenir une procédure pas à pas de l’analyseur de mémoire managée, consultez [utilisation de Visual Studio 2013 pour diagnostiquer les problèmes de mémoire .net en production](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/) sur le blog Visual Studio ALM + Team Foundation Server.  
  
## <a name="BKMK_Contents"></a> Sommaire  
 [Utilisation de la mémoire dans les applications .NET Framework](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identifier un problème de mémoire dans une application](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Collecter les instantanés de la mémoire](#BKMK_Collect_memory_snapshots)  
  
 [Analyser l’utilisation de la mémoire](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a>Utilisation de la mémoire dans les applications .NET Framework  
 .NET Framework étant un runtime avec Garbage Collection, dans la plupart des applications l'utilisation de la mémoire n'est pas un problème. Par contre, avec les applications de longue durée telles que les applications et les services web, et sur les appareils avec une quantité de mémoire limitée, l'accumulation d'objets en mémoire peut avoir un impact sur les performances de l'application et de l'appareil. Une utilisation excessive de la mémoire peut priver l'application et l'ordinateur de ressources si le garbage collector s'exécute trop souvent ou si le système d'exploitation est contraint de déplacer de la mémoire entre la RAM et le disque. Dans le pire des cas, une application peut se bloquer avec une exception « Mémoire insuffisante ».  
  
 Le *tas managé* .net est une région de mémoire virtuelle où sont stockés les objets de référence créés par une application. La durée de vie des objets est gérée par le garbage collector. Le garbage collector utilise des références pour effectuer le suivi des objets qui occupent des blocs de mémoire. Une référence est créée quand un objet est créé et assigné à une variable. Un même objet peut avoir plusieurs références. Par exemple, des références supplémentaires à un objet peuvent être créées en ajoutant l’objet à une classe, une collection ou autre structure de données ou en assignant l’objet à une seconde variable. Une référence peut aussi être créée quand un objet ajoute un gestionnaire à l'événement d'un autre objet. Dans ce cas, le second objet contient la référence au premier jusqu'à ce que le gestionnaire soit supprimé de manière explicite ou que le second objet soit détruit.  
  
 Pour chaque application, le garbage collector tient à jour une arborescence de références qui assure le suivi des objets référencés par l’application. L' *arborescence de référence* a un ensemble de racines, qui inclut des objets globaux et statiques, ainsi que des piles de threads associées et des objets instanciés dynamiquement. Un objet est enraciné si au moins l'un de ses objets parents y fait référence. Le garbage collector peut récupérer la mémoire d'un objet uniquement quand aucun autre objet ou variable dans l'application n'y fait référence.  
  
 ![Revenir en haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a>Identifier un problème de mémoire dans une application  
 Le symptôme le plus visible des problèmes de mémoire est le niveau de performances de votre application, en particulier s'il diminue au fil du temps. Une dégradation des performances d'autres applications pendant que votre application est en cours d'exécution peut également indiquer qu'il existe un problème de mémoire. Si vous soupçonnez un problème de mémoire, utilisez un outil tel que le gestionnaire des tâches ou l' [Analyseur de performances Windows](https://technet.microsoft.com/library/cc749249.aspx) pour approfondir vos recherches. Par exemple, une augmentation de la taille totale de mémoire que vous ne pouvez pas expliquer peut être envisagée comme une source possible de fuites de mémoire :  
  
 ![Croissance de la mémoire cohérente dans moniteur de ressource](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Vous pourriez également remarquer des pointes de mémoire plus élevées que ce que votre connaissance du code pourrait suggérer. Cela pourrait être le signe d'une utilisation inefficace de la mémoire dans une procédure :  
  
 ![Pics de mémoire dans Gestionnaire des ressources](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a>Collecter les instantanés de la mémoire  
 L’outil d’analyse de la mémoire analyse les informations des *fichiers dump* qui contiennent des informations sur les tas. Vous pouvez créer des fichiers dump dans Visual Studio, ou vous pouvez utiliser un outil tel que [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) à partir de [Windows Sysinternals](https://technet.microsoft.com/sysinternals). Consultez [qu’est-ce qu’un vidage et comment en créer un ?](https://blogs.msdn.microsoft.com/debugger/2009/12/30/what-is-a-dump-and-how-do-i-create-one/) sur le blog de l’équipe du débogueur Visual Studio.  
  
> [!NOTE]
> La plupart des outils peuvent recueillir des informations de dump avec ou sans données de mémoire de tas complètes. L'analyseur de mémoire de Visual Studio nécessite des informations de tas complètes.  
  
 **Pour collecter un vidage à partir de Visual Studio**  
  
1. Vous pouvez créer un fichier dump pour un processus qui a été démarré à partir d'un projet Visual Studio ou vous pouvez attacher le débogueur à un processus en cours d'exécution. Consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Arrêtez l'exécution. Le débogueur s’arrête lorsque vous choisissez **arrêter tout** dans le menu **Déboguer** , ou à une exception ou à un point d’arrêt  
  
3. Dans le menu **Déboguer** , choisissez **enregistrer le dump sous**. Dans la boîte de dialogue **enregistrer le dump sous** , spécifiez un emplacement et assurez-vous que **Minidump avec segment mémoire** (par défaut) est sélectionné dans la liste **type de fichier** .  
  
   **Pour comparer deux instantanés de mémoire**  
  
   Pour analyser l'augmentation de l'utilisation de la mémoire par une application, recueillez deux fichiers dump à partir d'une même instance de l'application.  
  
   ![Revenir en haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a>Analyser l’utilisation de la mémoire  
 [Filtrer la liste des objets](#BKMK_Filter_the_list_of_objects) **&#124;** [analyser les données de mémoire dans à partir d’un instantané](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** unique [comparer deux instantanés de mémoire](#BKMK_Compare_two_memory_snapshots)  
  
 Pour analyser un fichier dump à la recherche de problèmes de mémoire  
  
1. Dans Visual Studio, choisissez **fichier**, **ouvrir** et spécifiez le fichier dump.  
  
2. Dans la page **Résumé du fichier Minidump** , choisissez **Déboguer la mémoire managée**.  
  
    ![Page Résumé du fichier dump](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   L'analyseur de mémoire démarre une session de débogage pour analyser le fichier et affiche les résultats dans la page Affichage du tas :  
  
   ![Revenir en haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a>Filtrer la liste des objets  
 Par défaut, l'analyseur de mémoire filtre la liste d'objets dans un instantané de la mémoire pour afficher uniquement les types et instances codés par un utilisateur et uniquement les types dont la taille inclusive totale dépasse un seuil de pourcentage de la taille totale du tas. Vous pouvez modifier ces options dans la liste **afficher les paramètres** :  
  
|||  
|-|-|  
|**Activer Uniquement mon code**|Uniquement mon code masque les objets système les plus courants. Ainsi, seuls les types que vous créez figurent dans la liste.<br /><br /> Vous pouvez également définir l’option Uniquement mon code dans la boîte de dialogue **options** de Visual Studio. Dans le menu **Déboguer** , choisissez **Options et paramètres**. Sous l’onglet **débogage**/**général** , sélectionnez ou désactivez **uniquement mon code**.|  
|**Réduire les petits objets**|**Réduire les petits objets** masque tous les types dont la taille inclusive totale est inférieure à 0,5% de la taille totale du tas.|  
  
 Vous pouvez également filtrer la liste de types en entrant une chaîne dans la zone de **recherche** . La liste affiche uniquement les types dont le nom contient la chaîne.  
  
 ![Revenir en haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a>Analyser les données de mémoire dans à partir d’un instantané unique  
 Visual Studio démarre une nouvelle session de débogage pour analyser le fichier et affiche les données de mémoire dans une fenêtre Affichage du tas.  
  
 ![Liste des types d’objets](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Revenir en haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Table Type d'objet  
 La table du haut mentionne les types d'objets contenus en mémoire.  
  
- **Nombre** indique le nombre d’instances du type dans l’instantané.  
  
- **Taille (octets)** est la taille de toutes les instances du type, à l’exclusion de la taille des objets auxquels elle contient des références. La clé publique du signataire doit être fournie à la classe  
  
- La **taille inclusive (octets)** inclut la taille des objets référencés.  
  
  Vous pouvez choisir l’icône des instances (![l’icône d’instance dans la colonne type d’objet](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) dans la colonne **type d’objet** pour afficher une liste des instances du type.  
  
#### <a name="instance-table"></a>Table Instance  
 ![Table d’instances](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- L' **instance** est l’emplacement de mémoire de l’objet qui sert d’identificateur d’objet de l’objet.  
  
- **Valeur** indique la valeur réelle des types valeur. Vous pouvez placer le pointeur de la souris sur le nom d'un type référence pour afficher ses valeurs de données dans une bulle d'informations.  
  
   ![Valeurs d’instance dans une bulle d’informations](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Taille (octets)** est la taille de l’objet, à l’exclusion de la taille des objets auxquels il contient des références. La clé publique du signataire doit être fournie à la classe  
  
- La **taille inclusive (octets)** inclut la taille des objets référencés.  
  
  Par défaut, les types et les instances sont triés par **taille inclusive (octets)** . Pour changer l'ordre de tri, choisissez un en-tête de colonne dans la liste.  
  
#### <a name="paths-to-root"></a>Chemins d’accès à la racine  
  
- Pour un type sélectionné dans la table **type d’objet** , la table **chemins d’accès à la racine** affiche les hiérarchies de types uniques qui mènent aux objets racines pour tous les objets du type, ainsi que le nombre de références au type qui se trouve au-dessus de lui dans la hiérarchie.  
  
- Pour un objet sélectionné à partir de l’instance d’un type, **chemins d’accès à la racine** affiche un graphique des objets réels qui contiennent une référence à l’instance. Vous pouvez placer le pointeur de la souris sur le nom de l'objet pour afficher ses valeurs de données dans une bulle d'informations.  
  
#### <a name="referenced-types--referenced-objects"></a>Types référencés / Objets référencés  
  
- Pour un type sélectionné dans la table **type d’objet** , l’onglet **types référencés** affiche la taille et le nombre de types référencés détenus par tous les objets du type sélectionné.  
  
- Pour une instance sélectionnée d’un type, les **objets référencés** affichent les objets détenus par l’instance sélectionnée. Vous pouvez placer le pointeur de la souris sur le nom pour afficher ses valeurs de données dans une bulle d'informations.  
  
  **Références circulaires**  
  
  Un objet peut faire référence à un second objet qui détient directement ou indirectement une référence au premier objet. Lorsque l’analyseur de mémoire rencontre cette situation, il cesse d’étendre le chemin d’accès de référence et ajoute une annotation **[cycle détecté]** à la liste du premier objet et s’arrête.  
  
  **Types racine**  
  
  L'analyseur de mémoire ajoute des annotations aux objets racines qui décrivent le genre de référence détenu :  
  
|Annotation|Description|  
|----------------|-----------------|  
|`VariableName` de **variables statiques**|Variable statique. `VariableName` est le nom de la variable.|  
|**Handle de finalisation**|Référence à partir de la file d'attente de finaliseur|  
|**Variable locale**|Variable locale.|  
|**Handle fort**|Handle à une référence forte tiré de la table de handles d'objets.|  
|**Async. Handle épinglé**|Objet épinglé asynchrone tiré de la table de handles d'objets.|  
|**Handle dépendant**|Objet dépendant tiré de la table de handles d'objets.|  
|**Handle épinglé**|Référence forte épinglée tirée de la table de handles d'objets.|  
|**Handle RefCount**|Objet contenant des références tiré de la table de handles d'objets.|  
|**Handle handle sizedref**|Handle fort qui conserve une taille approximative de la fermeture collective de tous les objets et racines d’objets au moment du Garbage Collection.|  
|**Variable locale épinglée**|Variable locale épinglée.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a>Comparer deux instantanés de mémoire  
 Vous pouvez comparer deux fichiers dump d'un processus pour rechercher les objets susceptibles de provoquer des fuites de mémoire. L'intervalle entre la collecte du premier fichier (plus ancien) et du second fichier (plus récent) doit être suffisamment élevé pour que l'augmentation du nombre d'objets ayant fuit soit facile à détecter. Pour comparer deux fichiers  
  
1. Ouvrez le deuxième fichier de vidage, puis choisissez **Déboguer la mémoire managée** dans la page **Résumé du fichier Minidump** .  
  
2. Dans la page rapport d’analyse de la mémoire, ouvrez la liste **Sélectionner une ligne de base** , puis choisissez **Parcourir** pour spécifier le premier fichier de vidage.  
  
   L’analyseur ajoute des colonnes au volet supérieur du rapport qui affichent la différence entre le **nombre**, la **taille**et la **taille inclusive** des types par rapport aux valeurs de l’instantané précédent.  
  
   ![Colonnes DIFF dans la liste de types](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   Une colonne **diff du décompte de références** est également ajoutée à la table **chemins d’accès à la racine** .  
  
   ![Revenir en haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
## <a name="see-also"></a>Voir aussi  
 Blog [VS ALM TFS : Utilisation de Visual Studio 2013 pour diagnostiquer les problèmes de mémoire .NET dans](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)de production    
 [Analyse de &#124; la mémoire gérée de &#124; Visual Studio TV pour Channel 9](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Analyse de &#124; la mémoire managée de la boîte à outils &#124; Visual Studio Channel 9 dans Visual Studio 2013](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)