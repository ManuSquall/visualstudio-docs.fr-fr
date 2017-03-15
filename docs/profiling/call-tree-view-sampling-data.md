---
title: "Mode Arborescence des appels - donn&#233;es d’&#233;chantillonnage du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "méthode de profilage par échantillonnage, mode Arborescence des appels"
  - "Mode Arborescence des appels"
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Mode Arborescence des appels - donn&#233;es d’&#233;chantillonnage du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Arborescence des appels affiche les chemins d'accès d'exécution des fonctions parcourus dans l'application profilée.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans windows 8 et Windows Server 2012 requises des modifications significatives de la manière que le profileur Visual Studio collecte des données sur ces plateformes.  Les applications de mémoire de fenêtres requièrent également de nouvelles techniques de collection.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 La racine de l'arborescence correspond au point d'entrée de l'application ou du composant.  Chaque nœud de fonction répertorie toutes les fonctions appelées et les données de performance liées à ces appels de fonction.  
  
 Valeurs dans la vue Arborescence des appels pour les instances de fonction qui ont été appelées par la fonction parente dans l'arborescence des appels.  Les valeurs en pourcentage sont calculées en comparant la valeur de l'instance de la fonction au nombre total d'échantillons dans l'exécution du profilage.  
  
## Mise en surbrillance du chemin réactif d'exécution  
 La vue Arborescence des appels peut développer et mettre en surbrillance le chemin d'exécution de la fonction ou du processus qui a été le plus souvent échantillonné.  Pour afficher le chemin le plus actif, cliquez avec le bouton droit sur le processus ou la fonction, puis cliquez sur **Développer le chemin réactif**.  
  
## Définition du nœud racine de l'arborescence des appels  
 Chaque processus de l'exécution du profilage s'affiche sous la forme d'un nœud racine.  Vous pouvez définir le nœud initial de la vue Arborescence des appels en cliquant avec le bouton droit sur le nœud que vous souhaitez définir comme nœud de démarrage, puis en sélectionnant **Définir la racine**.  
  
 En définissant le nœud racine, vous supprimez toutes les autres entrées de l'affichage, à l'exception de la sous\-arborescence du nœud sélectionné.  Pour réinitialiser le nœud racine sur le nœud d'origine, cliquez avec le bouton droit dans la fenêtre de la vue Arborescence des appels, puis sélectionnez **Réinitialiser la racine**.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**ID de processus**|ID du processus \(PID\) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom de module**|Nom du module qui contient la fonction.|  
|**Chemin de module**|Chemin d'accès du module qui contient la fonction.|  
|**Source File**|Fichier source qui contient la définition de cette fonction.|  
|**Nom de la fonction**|Nom complet de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Adresse de la fonction**|Adresse de la fonction.|  
|**Niveau**|Profondeur de cette fonction dans l'arborescence des appels.  Uniquement dans les rapports en ligne de commande de [VSPerfReport](../profiling/vsperfreport.md).|  
|**Exemples exclusifs**|Nombre d'échantillons collectés dans cette fonction lorsqu'elle a été appelée par la fonction parent dans l'arborescence des appels.  Ce nombre ne comprend pas les échantillons qui ont été collectés dans les fonctions appelées par la fonction.|  
|**% d'échantillons exclusifs**|Pourcentage de tous les échantillons au cours de l'exécution du profilage qui correspondaient à des échantillons exclusifs de cette fonction lorsqu'elle a été appelée par la fonction parent dans l'arborescence des appels.|  
|**Exemples inclusifs**|Nombre d'échantillons collectés dans cette fonction lorsqu'elle a été appelée par la fonction parent dans l'arborescence des appels.  Ce nombre comprend les échantillons qui ont été collectés dans les fonctions appelées par la fonction.|  
|**% d'échantillons inclusifs**|Pourcentage de tous les échantillons au cours de l'exécution du profilage qui correspondaient à des échantillons inclusifs de cette fonction lorsqu'elle a été appelée par la fonction parent dans l'arborescence des appels.|  
  
## Voir aussi  
 [Comment : personnaliser les colonnes de la vue de rapport](../profiling/how-to-customize-report-view-columns.md)   
 [Call Tree View \- Profiler Sampling Data](../profiling/call-tree-view-sampling-data.md)   
 [Mode Arborescence des appels \- échantillonnage](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Mode Arborescence des appels \- instrumentation](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Mode Arborescence des appels](../profiling/call-tree-view-instrumentation-data.md)